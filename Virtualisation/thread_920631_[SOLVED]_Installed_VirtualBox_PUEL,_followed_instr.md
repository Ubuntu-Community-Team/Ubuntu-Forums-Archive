---
title: "[SOLVED] Installed VirtualBox PUEL, followed instructions, still can't access USB"
date: 2008-09-15
forum: Virtualisation
---

### Post by Jordanwb on 2008-09-15
I went to the VirtualBox website and followed the instructions to get the PUEL (or is PEUL?) version, I installed it, added my user to the vboxusers group and rebooted. I followed [these]("https://help.ubuntu.com/community/VirtualBox") instructions (someone found it necessary to make it secured), but I still can't configure USB (see pic). I get the same error for network, audio etc.

[Edit]Rebooting helps. <_<

---

### Post by howefield on 2008-09-15
There are 2 steps that I need to do to get USB working in the PUEL version of Virtualbox, they are...

Step one - type the following into a terminal uncomment as follows.

sudo gedit /etc/init.d/mountdevsubfs.sh

Uncomment the last 4 lines above to look like this:
#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

Step Two - type the following into a terminal and add the last two lines to it and save. You might need to reboot for this to take effect.

sudo gedit /etc/fstab

## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0

---

### Post by howefield on 2008-09-15
Also, when you load Virtualbox up, go into the settings for your VM and check the boxes for USB, Audio, ect ect as required.

---

### Post by tsbaker on 2008-10-30
I followed these instructions word for word literally, like copied and pasted in the terminal. I should mention that I'm running Intrepid 8.10. When type in `sudo gedit /etc/init.d/mountdevsubfs.sh` I do not see what you have posted. The output I'm getting is:



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

Am I doing something wrong, or this due to the fact that I'm running 8.10 and thus the release is to new. Just curious. The only reason I even need to run MS virtually is to sync my 2.1 iphone with iTunes. Thanks in advance

---

### Post by howefield on 2008-11-03
The above instructions were for 8.04.

---

### Post by howefield on 2008-11-03
Try the answer in this thread

[http://ubuntuforums.org/showthread.php?t=962726&highlight=usb+intrepid+virtualbox](http://ubuntuforums.org/showthread.php?t=962726&highlight=usb+intrepid+virtualbox)

worked for me.

---

