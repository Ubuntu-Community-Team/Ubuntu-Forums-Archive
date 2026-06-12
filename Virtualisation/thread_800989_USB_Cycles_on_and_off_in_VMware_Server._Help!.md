---
title: "USB Cycles on and off in VMware Server. Help?!"
date: 2008-05-20
forum: Virtualisation
---

### Post by mistakenidentity on 2008-05-20
Hey everyone,

I'm currently on a Lenovo T61p and have Ubuntu 8.04 installed as primary OS, and VMware Server running XP Pro. Everything works great, except for one problem… the USB port seems to cycle on and off. I edited the config file to allow USB devices, so I can see the device, however the devices turns on and off repeatedly. 

For example, VMware can see my USB device, the Motorola Q. I go to sync my Motorola Q, it starts to Sync, and then the USB keeps cycling on and off on the VMware machine using XP what seems to be like 8 second intervals. It will loose the USB connection, indicated by the blue circle icon, and it’ll just come back up and it will try to sync again. 

I can’t figure this out, can anyone suggest anything?

---

### Post by fjgaude on 2008-05-20
Have you tried putting this as the last line in your /etc/fstab file:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

And then reboot?

I don't know what version of Ubuntu you are using but maybe uncomment lines 42-45 starting with #mkdir -p /dev/bus/usb/.usbfs

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Like so:

```
    	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

I don't have any other suggestions... other than I'm sure you have loaded the driver for the Motorola device?

---

### Post by mistakenidentity on 2008-05-20
My version of Ubuntu is 8.04 i386 desktop version.

I added # USB for vmware/vbox
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0 to the /etc/fstab file to get the USB port recognized in the first place. 

As per your suggestion, I added usbfs /proc/bus/usb usbfs auto 0 0 to the /etc/fstab file, restarted, and doesn't work... so I removed it. 

Before I try the second suggestion of "uncommenting lines 42-45 starting with #mkdir -p /dev/bus/usb/.usbfs", should I leave in the usbfs /proc/bus/usb usbfs auto or leave it out?

Thanks for the help so far.

And as far as the drivers, yes, it's installed but is only up and running when the USB cycles on, but is off when it cycles off.

---

### Post by fjgaude on 2008-05-20
My experience is the fstab line makes some USB drives be recongized... usually USB printers and scanner don't need that line, just drives. I'd leave it in.

Your situation is most unusual... it's the kind of thing that very hard to pen down.

---

### Post by mistakenidentity on 2008-05-20
Well, crap. Thanks a lot for your help though. Much appreciated.

---

### Post by mistakenidentity on 2008-05-20
As far as the the second suggestion of "uncommenting lines 42-45 starting with #mkdir -p /dev/bus/usb/.usbfs",  here's what my code looks like with out any editing...
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          mountdevsubfs mountvirtfs
# Required-Start:    mountkernfs
# Required-Stop:
# Default-Start:     S
# Default-Stop:
# Short-Description: Mount special file systems under /dev.
# Description:       Mount the virtual filesystems the kernel provides
#                    that ordinarily live under the /dev filesystem.
### END INIT INFO

PATH=/lib/init:/sbin:/bin
TTYGRP=5
TTYMODE=620
[ -f /etc/default/devpts ] && . /etc/default/devpts

TMPFS_SIZE=
[ -f /etc/default/tmpfs ] && . /etc/default/tmpfs

KERNEL="$(uname -s)"

. /lib/lsb/init-functions
. /lib/init/mount-functions.sh

do_start () {
	#
	# Mount a tmpfs on /dev/shm
	#
	SHM_OPT=
	[ "${SHM_SIZE:=$TMPFS_SIZE}" ] && SHM_OPT="-osize=$SHM_SIZE"
	domount tmpfs shmfs /dev/shm $SHM_OPT

	#
	# Mount /dev/pts. Create master ptmx node if needed.
	#
	domount devpts "" /dev/pts -ogid=$TTYGRP,mode=$TTYMODE

	#
	# Magic to make /proc/bus/usb work
	#
	#mkdir -p /dev/bus/usb/.usbfs
	#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	#ln -s .usbfs/devices /dev/bus/usb/devices
	#mount --rbind /dev/bus/usb /proc/bus/usb
}

case "$1" in
  "")
	echo "Warning: mountdevsubfs should be called with the 'start' argument." >&2
	do_start
	;;
  start)
	do_start
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	# No-op
	;;
  *)
	echo "Usage: mountdevsubfs [start|stop]" >&2
	exit 3
	;;
esac
```

Do those errors mean anything?

---

### Post by fjgaude on 2008-05-20
Well, at least try commenting out the four lines as suggested. Using 8.04 I not sure what that does anymore... as the alpha and beta came online we went through many things to keep vmware and vbox running.

I'd try to remove the driver from Windows and then reload it to see if that changed anything.

---

