---
title: "QEMU managedsaved and restore on reboot and boot"
date: 2023-05-09
forum: Virtualisation
---

### Post by Eazy© on 2023-05-09
Hi!

Have just started to use QEMU after using Virtualbox for several years. One thing i used to do in Virtualbox is to use a script to automatically set my VM in saved state when I reboot the host and then restore my VM on boot.

I was hoping to do the same in QEMU but there are some problems...
In QEMU there is option in virt-manager to save, but when I restore the VM, the USB device I have added does not seem to be restored and I have to redirect it manually.
The USB device is also lost when I in console use:
```
virsh managedsave guest
virsh start guest
```

If my problem with the USB device is possible to solve, then I need to figure out how to best do to have my VM automatically saved before reboot and then restored at boot.
With Virtualbox I had a script in init.d. Should take the same approach with QEMU or is there a way to do it by editing a xml in QEMU's configs?

---

### Post by MAFoElffen on 2023-05-09
When you add a USB device in the viewer, it is temporary and lost in reboot, because that is not a persistent setting. Rather, if you add the USB in the virt-manager VM settings, Add Hardware, USB pass-through... then the setting is persistent (added to the Domain XML), and will survive a reboot.

The problem created by that, though, is that the USB device then always needs to be there for the VM to start.

So there is a tradeoff there. (cause and effect)

---

### Post by Eazy© on 2023-05-10
The USB device is lost even if I use virt-manager to save and then restore, and i have to manually redirect the device.
 
I don't have much patience to tinker with thing as i did in my younger years, so I think I give up and do everything manually. 
Seems only Virtualbox is able to do what want automatically, but as it uses 60% CPU its not a choice...

---

### Post by MAFoElffen on 2023-05-10
Please post the output of this command from your host within code tags
```

lsusb -v

```
Indicate which device is the one you are using in your VM.

Do a cold shutdown. Boot up fresh, and post the output of the command ran again... Let's compare the result to see if the "USB device" is changed in it's specific ID.

EDIT: As I remember, this might have been a problem that I ran into before...

---

### Post by Eazy© on 2023-05-10
> **MAFoElffen said:**
> Please post the output of this command from your host within code tags
```

lsusb -v

```
Indicate which device is the one you are using in your VM.

Do a cold shutdown. Boot up fresh, and post the output of the command ran again... Let's compare the result to see if the "USB device" is changed in it's specific ID.

EDIT: As I remember, this might have been a problem that I ran into before...

The  ID is identical before and after a cold boot.

Before:

```
  idVendor           0x1781 Multiple Vendors
  idProduct          0x0c31 Telldus TellStick Duo
```

After cold boot:

```
  idVendor           0x1781 Multiple Vendors
  idProduct          0x0c31 Telldus TellStick Duo
```

This is how I set up my USB device in virt-manager
[http://www.bronsaldersvagen.se/Eazy/before_reboot.png](http://www.bronsaldersvagen.se/Eazy/before_reboot.png)

I have no problem with my USB device when doing normal reboot/boot. The device adds fine rebooting/booting my host, or only start/stop my VM. It is when I try to save and then start my VM (just as Virtulabox "saved state") the USB does not activate and I have to, in virt-manager, click on "redirect usb-device". 

One possible solution (that i just thought of when writing this post) is to remove the device in virt-manager and only use virsh commands (then make a script).
I'm just guessing, and I don't know what commands/syntax to use, or if there are any that do what I want.

---

### Post by MAFoElffen on 2023-05-10
> **Eazy© said:**
> One possible solution (that i just thought of when writing this post) is to remove the device in virt-manager and only use virsh commands (then make a script).
I'm just guessing, and I don't know what commands/syntax to use, or if there are any that do what I want.
You would create an xml file containing the XML snippet for the USB Device...
```

<hostdev mode="subsystem" type="usb" managed="yes">
  <source>
    <vendor id="Ox1781"/>
    <product id="0x0c31"/>
  </source>
<hostdev>

```
The 'address' and 'alias' lines are optional for this file.  

Lets say you named it "TellStickDuo.xml".

Then you would use this Virsh command to attach it to the Domain, while it is running... Lets say it was name MyDomain01
```

sudo virsh attach-device MyDomain01 --file /home/Documents/TellStickDuo.xml --current

```
With that last option, --current takes effect for the current running Domain. --config makes the change on the next reboot. --persistent make the change persistent.

To hot-unplug it, while the domain is running, then do
```

sudo virsh detach-device MyDomain01 --file /home/Documents/TellStickDuo.xml

```

---

### Post by Eazy© on 2023-05-11
I have come a bit further with your help. Thank you very much! You are very helpful!

This is how I need to do to make this work:

Set the VM in saved state:
```
sudo virsh managedsave win10
```

Start the VM from saved state (command one by one):
```
sudo virsh start win10
sudo virsh detach-device win10 --file /home/bserver/tellstick.xml --current
sudo virsh attach-device win10 --file /home/bserver/tellstick.xml --current
```

It does not matter if i use --persistent or --current, I need to detach the device and then attach or the device wont show up.
I don't know if there is a better way to do this.

I believe I need to in virt-manager remove to not start at boot and use above virsh commands in a script and add it in either init.d, or make a systemctl service. Dont know which is better...

---

### Post by MAFoElffen on 2023-05-11
> **Eazy© said:**
> I believe I need to in virt-manager remove to not start at boot and use above virsh commands in a script and add it in either init.d, or make a systemctl service. Dont know which is better...
I'm wondering if doing this would be better: [https://libvirt.org/hooks.html](https://libvirt.org/hooks.html)

Not sure of the timing of it... But I think this part matches the timing:
> 
The third location, 0.9.13 , occurs after the QEMU process has successfully started up:
```

/etc/libvirt/hooks/qemu guest_name started begin -

```

Then mark it as autostart...

That way, each time that VM was loaded, the hooks would kick off your script automatically. Right?

EDIT:
RE: [https://passthroughpo.st/simple-per-vm-libvirt-hooks-with-the-vfio-tools-hook-helper/](https://passthroughpo.st/simple-per-vm-libvirt-hooks-with-the-vfio-tools-hook-helper/) (As how it actually works and examples)

---

### Post by MAFoElffen on 2023-05-11
It looks like if you created the folder structure '/etc/libvirt/hooks/qemu.d/win10/started/begin/'... put your script in that folder, and made it executable... that it would start that script, each time, after Domain 'win10' was started...

---

### Post by Eazy© on 2023-05-16
I took a break from solving this. Got tired when I couldn't figure out how to set the VM automatically in managedsave on host reboot/shutdown. Could probably solve the rest with the help you provided. 
Seems what I'm trying to do is not something that is requested widely, so google does not give me much help. I might return solving this. Will give a guide if I do.

Thanx again for your help!!

---

### Post by MAFoElffen on 2023-05-16
I have been using QEMU hooks for Intel GVT-G virtual GPU's... Where on pre-load of the VM, I add modules to the Host's kernel, then after boot of the VM, add vGPU devices to the system, for use with the VM... Then on shutdown/reboot of the VM, remove the virtual graphics devices. 

Sort of like a pass-through vfio devices in an iommu protected environment. Except with virtual devices being defined and shared... Instead of a physical pass-through.

That link I posted explains how the process of QEMU Hooks works logically, and the directory structure that provides for that.

---

