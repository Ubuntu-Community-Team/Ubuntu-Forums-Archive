---
title: "virtualbox- Windows xp usb wont work"
date: 2008-04-18
forum: Virtualisation
---

### Post by scottc992004 on 2008-04-18
I have tried everything but my hard drives won't show in windows xp pro in virtualbox ver 1.5.6. 

using gksu gedit /etc/init.d/mountdevsubfs.sh  :

#Magic to make /proc/bus/usb work
	
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb

and

using sgedit /etc/udev/rules.d/40-permissions.rules  :

# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device",		MODE="0666"


i don't know how to get it working plz help.

---

### Post by kerry_s on 2008-04-18
did you turn it on in virtualbox?

i saw that setting for usb when i was using it, but i just uninstalled my virtualbox about 2 hours ago. wasn't worth running on my 450mhz 256mb ram rig, just to slow, for me anyways. :)

---

### Post by kyphi on 2008-04-19
1.  > virtualbox - Windows xp usb wont work

2.  > ... but my hard drives won't show in windows xp pro in virtualbox ver 1.5.6.

Have I got this straight - neither your USB nor your hard drives work in VirtualBox ?

Did you install the correct version of VBox - if you are using Feisty it should be the Feisty version.

Have you installed the guest additions ?

---

### Post by Life On Mars on 2008-04-25
> **scottc992004 said:**
> I have tried everything but my hard drives won't show in windows xp pro in virtualbox ver 1.5.6. 

using gksu gedit /etc/init.d/mountdevsubfs.sh  :

#Magic to make /proc/bus/usb work
	
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb

and

using sgedit /etc/udev/rules.d/40-permissions.rules  :

# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device",		MODE="0666"


i don't know how to get it working plz help.

Did you forget to do a restart?

```
sudo /etc/init.d/mountdevsubfs.sh start
```

---

### Post by PhrygianCat on 2009-04-29
First of all, make sure that you're not using the OSE version of VirtualBox from the repo. The non-OSE has more options, e.g. for USB. And make sure you uninstall the OSE version before installing the one from VirtualBox download site. And after the installation, check the settings of the guest to make sure you select option for the USB.

If after that the USB is still not working, update your /etc/fstab and add these 2 lines:

> #usbfs
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

I can't remember if you need to reboot after that or not. Good luck.

---

