---
title: "Smartcard reader"
date: 2008-01-28
forum: Virtualisation
---

### Post by masi0 on 2008-01-28
hello lads,

is there a way to use smartcard reader inside VM with XP SP2 on Ubuntu?
thats the only thing that keeps me from going to 7.10:(

thx

---

### Post by fjgaude on 2008-01-28
Sure, VMware handles just about all USB devices, cardreaders, printers, scanners, etc. Gutsy has four lines commented out that Feisty didn't. Can't say why the programmers did this but it is easy to fix:

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Uncomment lines 42-45 starting with #mkdir -p /dev/bus/usb/.usbfs

```
        mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

Save and exit. Reboot. Or simply run:

```
sudo etc/init.d/mountdevsubfs.sh start
```

You might have to add this line to your /etc/fstab file:

```
usbfs /proc/bus/usb usbfs auto 0 0 
```

That should do it. If you have problems let us know.

---

### Post by masi0 on 2008-01-31
fjgaude, really thanks for help - it seems it worked - vmware xp sees cardreader, however my laptop has pcmcia reader with smardcard on it so I am just wondering if there is any possibily to convince vmware linux to work with this as well?

tha:)

---

### Post by fjgaude on 2008-01-31
I don't know of a way. Others here may know. Start another thread just with that issue.

---

