---
title: "Getting a USB device to work"
date: 2011-05-19
forum: Virtualisation
---

### Post by Mark224 on 2011-05-19
[Win XP Host System using Oracle VirtualBox 4.  Ubuntu 9.10 Guest.]

I want to mount USB drives from the host into the guest OS.

I have installed the USB2 extensions for VirtualBox.
I have installed the USB host drivers.

When I mount the USB drive I can see the device listed in VirtualBox using the USB icon.  However I cannot see it from the
Ubuntu guest.  If I type:
```

sudo fdisk -l

```
it only shows the hard disks.

dmesg seems to have some errors but I don't understand what they mean.  Unfortunately I can't seem to copy/paste them at the moment but they are like "usb1-1: device desriptor read error -32".

The USB drive works fine when used on the host system. 
Please advise.

---

### Post by b0b138 on 2011-05-19
Make sure you are added to the vboxusers group

---

### Post by Mark224 on 2011-05-20
Isn't that just for Linux host systems?  There is no vboxusers group on my Linux guest OS.  I do have the host additions installed.

---

### Post by adipramono on 2011-05-22
I use my Ubuntu as the host and Windows XP as the guest OS and everything is ok :p

---

### Post by Mark224 on 2011-05-27
I get an error dialog "VirtualBox - Error"

Failed to attach the USB device Unknown device to the virtual machine

E_INVALIDARG (0x80070057)

---

