---
title: "USB on VMWare Server"
date: 2008-05-05
forum: Virtualisation
---

### Post by Th&#7883;t Lu&#7897;c on 2008-05-05
I install VMWare Server on Ubuntu 8.04. On menu, chose VM > Removable Devices > USB. But, when i go to virtual machine, example Windows XP and mount USB, it not have one.
Now, how to make virtual machine detect USB.
Thank you.

---

### Post by Lord_Phoenix on 2008-05-06
I think VMWare and VirtualBox have the same setup when it comes to USB so you might want to check this out.

[http://forum.notebookreview.com/showthread.php?t=242936t]("http://forum.notebookreview.com/showthread.php?t=242936t")

---

### Post by Th&#7883;t Lu&#7897;c on 2008-05-06
This is options for VirtualBox, not VMWare :(

---

### Post by fjgaude on 2008-05-06
> **Th&#7883 said:**
> I install VMWare Server on Ubuntu 8.04. On menu, chose VM > Removable Devices > USB. But, when i go to virtual machine, example Windows XP and mount USB, it not have one.
Now, how to make virtual machine detect USB.
Thank you.

Here's what will do the trick. In a terminal enter:

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Enter your password. We are now in gedit, using root permissions. Uncomment four lines in the file you are looking at starting with line #42. Do this by deleting the "#" in front of each of the four lines so that the lines look like this:

       ```
mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

Save the file and exit the editor. Next we will edit your fstab using the same gedit program, in a terminal enter:

```
gksudo gedit /etc/fstab
```

Enter your password. Then copy this line and paste it into the end of the file:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Save the file. Exit the editor. Reboot your computer.

---

### Post by Th&#7883;t Lu&#7897;c on 2008-05-07
Good work. Thanks fjgaude :)

---

### Post by billybowden on 2009-11-03
I don't think that you need to comment anything out. When I did it disabled my Konsole application. It works without commenting anything  out. Just append some the text you suggested to the end of the file.

---

### Post by texjeff on 2010-02-19
I appreciate any help on this, and I have read through a bunch of previous posts.  My configuration is:
 - Ubuntu 8.04 LTS - works great
 - VMware Server 2.02 - mostly works great
 - XP-SP3 client - mostly works great

I can access USB devices besides keyboard/mouse either thru Ubuntu directly, or on the XP VM when on the host system.

I cannot access USB devices (i.e. card reader) when using the XP VM from another machine (i.e. laptop).  The other features of the XP VM all work fine.  The USB issue is the problem.

I have applied the following tips from these forums:
 - VMware tools is installed on the XP VM, running fine.
 - USB controller is added to the hardware config for the XP VM
 - uncommented the 4 lines in /etc/init.d/mountdevsubfs.sh
 - added the line to /etc/fstab to mount usbfs
    "usbfs /proc/bus/usb usbfs auto 0 0"
 - also tried
   "usbfs /proc/bus/usb usbfs devgid=46,devmode=644 0 0"
 - chmod -R 777 /proc/bus/usb   #yes I know, temporarily unsafe
 - checked logs in /var/log/vmware
   > USB card reader not being found when XP is remote
 - hardware version of the VM is 7 (supports USB)

The server has been rebooted with each change.  And I tried different combos, with server reboots on each one.

When the XP VM is run from my laptop, all networking and everything else is fine.  Plugging in a USB device (card reader) does not result in any discovery.  The laptop XP discovers it fine.  The XP VM does not - when viewed in the hardware device manager.  And the VMware web console does not recognize it in the USB drop down either (it is not there at all).

There is probably one little change that will make it work, but it sure is eluding me!  Thanks in advance to anybody for help or suggestions.

---

### Post by dcstar on 2010-02-26
> **texjeff said:**
> 
........
**When the XP VM is run from my laptop**, all networking and everything else is fine.  Plugging in a USB device (card reader) does not result in any discovery.  The laptop XP discovers it fine.  The XP VM does not - when viewed in the hardware device manager.  And the VMware web console does not recognize it in the USB drop down either (it is not there at all).

There is probably one little change that will make it work, but it sure is eluding me!  Thanks in advance to anybody for help or suggestions.

You do not "run" a VM that is actually on another piece of hardware, you just access the console via the interface to the VM controller on that hardware.

AFAIK you cannot plug in hardware to a USB port on the remote device and expect it to be seen by the host VM device, you have to plug it in on the host device for the VM running on that host hardware to access it.

---

### Post by texjeff on 2010-02-26
Thanks David for confirming the USB behavior.  I know that USB keyboards and mice work since I tried different ones at the remote interface via my laptop.  But other USB devices don't work.  I guess VMware cut their losses by just supporting the bare minimum needed to work operationally with the VM.

From the installed host we are getting USB interaction just fine with different devices.  And the USB toggle button at the top of the host console is a nice feature for giving the ability to use the USB device on the host server or using the device on one of the VMs.

...Jeff

---

### Post by dcstar on 2010-02-27
> **texjeff said:**
> Thanks David for confirming the USB behavior.  I know that USB keyboards and mice work since I tried different ones at the remote interface via my laptop.  But other USB devices don't work.  I guess VMware cut their losses by just supporting the bare minimum needed to work operationally with the VM.

From the installed host we are getting USB interaction just fine with different devices.  And the USB toggle button at the top of the host console is a nice feature for giving the ability to use the USB device on the host server or using the device on one of the VMs.

...Jeff

If you want to actually run the VM on the laptop then you can install VMware Server on that laptop (the Windows version is also free) and actually run the VM files that are on the Linux server (which must not be running that VM) over a network.

It won't be quick, but is should work and you will have full USB support.

---

### Post by texjeff on 2010-02-28
Hi David - thanks for the second followup also.  That is a good point and a valid solution.

Jeff

---

