---
title: "Ubuntu USB USb"
date: 2008-01-20
forum: Virtualisation
---

### Post by shoeshrimp on 2008-01-20
Hey guys, I've installed Ubuntu on Virtual PC 2007 (getting over the mouse and some display problems), and am now not sure how to get it to detect any inserted USB devices in Ubuntu, rather than the host operating system. Any ideas??

Plus I can't seem to get my resolution at 1024x768.. it'll only let me use safe graphics mode (even though colour depth is 16).

Thanks for your help,

Tom

---

### Post by fjgaude on 2008-01-20
I don't know about what setup you have, but to get things fully working there are things that have to be done. First uncomment four lines like so:

```
gksudo gedit /etc/init.d/mountdevsubfs.sh

        mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

Uncomment lines 42-45 starting with #mkdir -p /dev/bus/usb/.usbfs like above.

Svfe, then in terminal do:

```
sudo /etc/init.d/mountdevsubfs.sh start
```

You might wish to add this line to your /etc/fstab file:

```
usbfs /proc/bus/usb usbfs auto 0 0  in the fstab file
```

Some have found this necessary for USB flash drives.

Let us know how you make out.

---

