---
title: "VMWare problem USB Connection"
date: 2008-05-10
forum: Virtualisation
---

### Post by benc123 on 2008-05-10
VMWare problem
I have XP virtualized on my 7.10 ubuntu laptop. It works well but i have a few problems that i need help with.

I cannot seem to get USB devices to mount on it. I installed VMware tools, and added the USB device controller but still no joy. When i go to the VM tab, removable devices, USB devices, it is empty. Even though my memory stick is mounted on my 'normal' Desktop.

I also cannot seem to drap and drop files between the too, it just comes up with
"Unable to open: Virtual machine "/home/benc/Desktop/Group Work jak..doc" is not in the inventory".

jak doc is a open office word doc. (saved in windows doc format)

I would appreciate any help you can give as i am at a complete loss.
Thanx benc123.

---

### Post by fjgaude on 2008-05-10
If you are using Ubuntu 8.04, released, the Sticky above this Forum should get you to see what you are missing: a single line to be added to /etc/fstab file at its bottom:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Let us know if you have further problems.

---

### Post by the_nite_owl on 2008-05-10
I have not tried the usbfs line that fjgaude shows above but I did find a command on the VMWare site to issue from a terminal.
sudo mount -t usbfs none /proc/bus/usb

I imagine this is more of a one time command rather than a permanent fix, I will have to try out the other.

I was having the exact same issue and once I issued the above command I could see all the USB devices that the Linux host could see.  My problem is that I am trying to get my WM6 smartphone recognized in the XP client and since Linux does not recognize it, the XP client will not recognize it either.

I am going to do some more searching on here for an answer and if not found post a message of my own.

Good luck.

---

### Post by fjgaude on 2008-05-10
Such works if you are using 8.04. If not, you have to fix four lines:

Uncomment lines 42-45 starting with #mkdir -p /dev/bus/usb/.usbfs

gksudo gedit /etc/init.d/mountdevsubfs.sh

Like so:

    	```

       mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

That with adding that line to /etc/fstab takes care of USB devices in vmware.

---

### Post by Nampla on 2008-05-14
if your using vmware server then you really dont have usb device support.  Vmware server 1.05 (and older) only support usb 1.1 (which is a dinasour and very few devices exsist) your best bet if it is just file xfer then use samba and share the folder.  I created a share folder in linux and a user.  then set up the user in windows.  there are plenty of tutorials out if ya need it.

Good Luck

---

### Post by fjgaude on 2008-05-14
> **Nampla said:**
> if your using vmware server then you really dont have usb device support.  Vmware server 1.05 (and older) only support usb 1.1 (which is a dinasour and very few devices exsist) your best bet if it is just file xfer then use samba and share the folder.  I created a share folder in linux and a user.  then set up the user in windows.  there are plenty of tutorials out if ya need it.

Good Luck

USB 1.1 works fine for printers and scanners... not so good for cameras. It's the speed limitation of 11Mb/sec versus the 450Mb/sec, or something like that.

---

### Post by l8niteequine on 2008-05-27
Hi. I have tried your fix to this problem (uncommenting lines 42-45 and adding that last line to /etc/fstab) and still am not able to see either a flash drive or external hard drive in my vm. I have 8.04 as a host and am using an XP Pro VM on one machine and a Windows Server 2000 VM on another. Is there anything else I can try to see the usb drives in my VM? Thank you.

---

### Post by fjgaude on 2008-05-27
The USBs show in VM/Removable Devices/USB Devices menu.

---

### Post by l8niteequine on 2008-05-28
The devices show up in the VM menu and are checked that they are connected, but never show up in the VM.

---

### Post by fjgaude on 2008-05-28
If you have the drivers loaded in the VM then I can't say what could be wrong... don't have any more suggestions.

---

### Post by l8niteequine on 2008-05-29
Thank you for your advice. We discovered yesterday that the drivers are not installed on those VMs.

---

