---
title: "[SOLVED] empty mountdevsubfs.sh??!!"
date: 2007-12-31
forum: Virtualisation
---

### Post by A-dogg on 2007-12-31
I'm trying to enable usb support in vbox and I opened my mountdevsubfs.sh file to edit it...

it's empty! 

can someone post (or tell me where to get) the original file? seems like it may have gotten erased somehow...

much thanks!!!!

---

### Post by dcstar on 2008-01-01
> **A-dogg said:**
> I'm trying to enable usb support in vbox and I opened my mountdevsubfs.sh file to edit it...

it's empty! 

can someone post (or tell me where to get) the original file? seems like it may have gotten erased somehow...

much thanks!!!!

Here is my /etc/init.d/mountdevsubfs.sh (make sure you have this name exactly right):

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
	# These following 4 lines were uncommented to make USB devices avabilable in vmware
	#
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
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

---

### Post by A-dogg on 2008-01-01
thanks you !!!!!

---

### Post by Gullien on 2009-11-22
Hello there,

I might come a bite late ... hope you still check that thread !!
I had the same problem as A-dogg, and copy past the code ... but usb controller is still not working.

By the way, my host OS is Ubuntu 9.10 and my guest one is XP ... any idea to make the usb recognized in my guest ??

Thanks in advance,
Gullien

---

### Post by Zoxel on 2010-05-19
How about Ubuntu 10.04 x86-64?
Will the script work for this distro too?

---

