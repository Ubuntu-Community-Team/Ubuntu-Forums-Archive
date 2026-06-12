---
title: "Virtualbox 1.6 + Hardy 8.04 64bit + USB = Doesn't work"
date: 2008-05-07
forum: Virtualisation
---

### Post by laserline on 2008-05-07
Hello,

I've just installed a fresh installation of Ubuntu 8.04 Hardy 64bit.
The system is fully updated.
Then, I've downloaded the approptiate virtualbox .deb file from the virtualbox site.

The guest (XP) has both USB options enabled, USB Controller and USB2.0 Controller.

I've created an XP guest, then got this error: "Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer."  I fixed that by  uncommented lines 41-44 and at file /etc/init.d/mountdevsubfs.sh
Then I ran sudo /etc/init.d/mountdevubds.sh start
And that problem was gone.
 
Now I try to attach a diskonkey and I get this error:
"not permitted to open the usb device check the usbfs virtualbox"

What do I need to do to fix this ??

Thanks,
Idan.

---

### Post by OldTimeTech on 2008-05-07
Check this conversation out here in the Virtualization forum....you will find the way to get the usb's to work...

[ubuntu] Black Screen / No USB with VirtualBox (Windows XP)

---

### Post by laserline on 2008-05-10
There was a typo in the Virtualbox wiki.

Here is the fix:
1. Uncomment lines 41-44 in file 
```
# sudo vi /etc/init.d/mountdevsubfs.sh
```
Locate the line starts with
```
 Magic to make /proc/bus/usb work
```
2. Run as root: sudo /etc/init.d/mountdevsubfs.sh start
3. Add the following line to /etc/fstab
```
# sudo vi /etc/fstab
```
```
usbfs           /proc/bus/usb   usbfs   devgid=124,devmode=0666 0 0
```
Where devgid is the group number of your vboxusers group.
4. Reboot.

Good Luck!

NOTE: You can use any editor you like (nano, gedit, etc...)

Idan.

---

### Post by veiloctane on 2008-08-08
thank you so much this helped and worked like a charm!!!

---

### Post by laplace/d on 2008-10-12
thanx!, that did it form me, there's only one problem....whenever i change fstab settings and add "usbfs           /proc/bus/usb   usbfs   devgid=124,devmode=0666 0 0"
the usb storage devices are mounted as read-only devices.

---

