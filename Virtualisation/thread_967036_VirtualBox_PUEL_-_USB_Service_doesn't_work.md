---
title: "VirtualBox PUEL - USB Service doesn't work"
date: 2008-11-01
forum: Virtualisation
---

### Post by JoeFlennigan on 2008-11-01
Hello,
I'm using the closed source version of Sun's VirtualBox-2.0 and Ubuntu 8.10. I always got this error:

```
 Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer. 
```


After playing a little arround, I got the message not to appear anymore. But my Guest-OS (WindowsXP) is not recognizing USB-Devices, when I plug one in.

In some how-tos it is recommended to open this file: "/etc/init.d/mountdevsubfs.sh" and to look for this lines:

```

# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

```





But my one looks this way:


```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          mountdevsubfs
# Required-Start:    mountkernfs
# Required-Stop:
# Should-Start:      udev
# Default-Start:     S
# Default-Stop:
# Short-Description: Mount special file systems under /dev.
# Description:       Mount the virtual filesystems the kernel provides
#                    that ordinarily live under the /dev filesystem.
### END INIT INFO
#
# This script gets called multiple times during boot
#

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
	[ "${SHM_SIZE:=$TMPFS_SIZE}" ] && SHM_OPT=",size=$SHM_SIZE"
	domount tmpfs shmfs /dev/shm tmpfs -onosuid,nodev$SHM_OPT

	#
	# Mount /dev/pts. Master ptmx node is already created by udev.
	#
        domount devpts "" /dev/pts devpts -onoexec,nosuid,gid=$TTYGRP,mode=$TTYMODE
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




What is wrong? I've tried this too, but it didn't help:

```

echo "none /proc/bus/usb usbfs devgid=$(grep plugdev /etc/group | sed 's/plugdev:x:\(.*\):.*/\1/'),devmode=664 0 0" | sudo tee -a /etc/fstab

```



Does anyone know a way to get the USB-Support working?

Thanks for answering!
P.S.: I did NOT forget to activate the USB-Option!


//EDIT:

I have added to /etc/fstab the following line, but didn't work too:

none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

---

### Post by uidb4056 on 2008-11-01
On 8.10 only is needed to add in /etc/fstab the next line

none /proc/bus/usb usbfs devgid=XXX,devmode=664 0 0

Being XXX the Group ID of vboxusers (see under System-Administration-Users and Groups).

Have you checked if 46 is the right Group ID of vboxusers group?.

---

