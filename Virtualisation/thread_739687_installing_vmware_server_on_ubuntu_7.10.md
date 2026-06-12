---
title: "installing vmware server on ubuntu 7.10"
date: 2008-03-30
forum: Virtualisation
---

### Post by Matt26 on 2008-03-30
can anyone direct me to instructions on how to get vmware server 1.0.5 build 80187 on ubuntu 7.10?  thanks.

---

### Post by upthelum on 2008-03-30
[http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)

---

### Post by Matt26 on 2008-03-30
sorry if i was unclear- i am looking for installation instructions.  thanks.

---

### Post by fjgaude on 2008-03-30
If this is not clear let us know and another shot will be made.

1. Get latest version, 1.0.5, of vmware server from vmware.com website. Log-in and get at the same time your free license number.

2. Install linux headers matching your kernel version, and build-essential using apt-get or Synaptic, if they are not already on your system.

3. Unpack the software

4. Then run

sudo ./vmware-install.pl

5. follow the guide using mostly the defaults, then

Uncomment lines 42-45 starting with #mkdir -p /dev/bus/usb/.usbfs

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

```

    	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

Then place in the fstab file this line:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Good to add this line into your guest .vmx file using text editor:

```
mainMem.useNamedFile=FALSE
```

You will have full copy, paste from host to and from guest, and USB device handling capability, drives, scanners, printers, etc.

Let us know how you are doing.

---

