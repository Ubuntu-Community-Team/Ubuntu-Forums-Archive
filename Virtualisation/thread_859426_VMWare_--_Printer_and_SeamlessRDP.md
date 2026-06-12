---
title: "VMWare -- Printer and SeamlessRDP"
date: 2008-07-14
forum: Virtualisation
---

### Post by MasterXandrex on 2008-07-14
OK, so I have a Lexmark X7170 that I have never been able to get to work in linux -- here's what I want to do. I have created a Windows XP VM -- I use it for MS Office 2007 and a few other things that I have to have windows for -- and I want to set it up and then use it via a share. I have the networking working but I cannot get the VM to detect the printer. I have given it a USB device, but I don't know how to connect a USB device to the VM... any help?

My other issue is that I would like to use SeamlessShellRDP with this VM to use my programs outside the VM window, but I can't get it to work. It's supposed to launch just the application in an XWindow, but every time I try in Hardy I get the whole environment. Any ideas?


Thanks,

Xan

---

### Post by MasterXandrex on 2008-07-14
Firstly, I would like to thank everyone for their help... :)

I've solved the first problem thusly; the following file (/etc/init/d/mountdevsubfs.sh) needs to have some lines (42-45) uncommented to make the proper device entries for VMWare server to use USB devices:

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

However, does anyone know about the seamlessshellRDP issue?


Xan

---

### Post by MasterXandrex on 2008-07-15
Bumpety... please someone.


Xan

---

### Post by bodhi.zazen on 2008-07-15
since your google seems broken :

    [https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)
    [https://wiki.ubuntu.com/SeamlessWindowsIntegration](https://wiki.ubuntu.com/SeamlessWindowsIntegration)
    [http://www.cendio.com/seamlessrdp/](http://www.cendio.com/seamlessrdp/)

---

### Post by MasterXandrex on 2008-07-17
Had I been able to find the answer in Google then I would have found it. I have indeed been searching -- in fact I had read each of those pages prior to posting and bumping. 

What I was asking is if anyone has been able to get it to work in Hardy. I've used it in Dapper, but since upgrading have been unable to get just the window, I get the whole environment. 

I was wanting to know if anyone has any idea what might be causing this particular behavior? Not simply how it should work...


Xan

---

### Post by zachtib on 2008-07-17
Not sure about your seemless issue, but VMware Workstation 6.5 has that sort of functionality built in with Unity mode.

---

