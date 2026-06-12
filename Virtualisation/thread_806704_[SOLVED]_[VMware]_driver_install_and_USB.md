---
title: "[SOLVED] [VMware] driver install and USB"
date: 2008-05-25
forum: Virtualisation
---

### Post by kakyoism on 2008-05-25
I've successfully set up XP on VMware on my Hardy,
now I wonder whether I need to install the REAL hardware driver 
on the virtual Windows....would I feel differently?

Also, I installed VM tools, but still the system does not recognize my USB harddrives, (empty USB device menu)

Any ideas?
Thx!!

---

### Post by diablo75 on 2008-05-25
> **kakyoism said:**
> I've successfully set up XP on VMware on my Hardy,
now I wonder whether I need to install the REAL hardware driver 
on the virtual Windows....would I feel differently?

Also, I installed VM tools, but still the system does not recognize my USB harddrives, (empty USB device menu)

Any ideas?
Thx!!

Open the following file: /etc/init.d/mountdevsubfs.sh by entering this in terminal:

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Find the following lines:
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb


Unmark them so that look like this:

mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb


Save, restart and your usb devices should be recognized.

As for your first question, no, you have no reason to install the real hardware drivers for your PC because the XP machine (as you'll discover, if you browse your Device Manager) is entirely simulated.  The hardware is simulated, that is.  So for instance, Windows XP has a "video card" which is actually just a special driver that feeds video into VMware Server to be displayed on screen inside a window.  However, USB devices are given strait bridged access when they're in use, which makes them inaccessible temporarily from Ubuntu.

---

### Post by fjgaude on 2008-05-25
If you are using 8.04 I believe all you need do is add this line to the bottom of your /etc/fstab file:

```
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

Reboot and then you will find your USB devices under VM/Removable Devices menu.

---

### Post by kakyoism on 2008-05-25
thank you both!

that worked out well!

---

