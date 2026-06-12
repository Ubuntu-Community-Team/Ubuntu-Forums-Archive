---
title: "Unable to mount usb printer"
date: 2010-04-29
forum: Server Platforms
---

### Post by gyzer on 2010-04-29
I am trying to mount my usb printer in Ubuntu Server 9.10. I'm trying to do this so that the usb printer will be picked up by vmware server so the Windows XP guest I have on there will then be able to access the printer as if it were hooked up to it directly. I found a few posts online and this is what I've done so far.

I found in a couple of posts that they said I should uncomment out the following lines in /etc/init.d/mountdevsubfs.sh. Well I found that the file didn't exsist. Someone posted up their copy of it so I copied that code into the mountdevsubfs.sh script. That code is the following:

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

```I also added this line to the bottom of my /etc/fstab file

```
usbfs /proc/bus/usb usbfs auto 0 0
```When I go ahead and run the script it errors out on this line: 

```
. /lib/init/mount-functions.sh
```I went to go look in /lib/init and the mount-functions.sh script doesn't exist. I've googled this and I haven't been able to find anything.

Am I doing this the right way or is there a better way to go about doing this? If this is the right way, why am I missing /lib/init/mount-functions.sh and how can I get that script?

Thanks in advanced for the help

---

### Post by gyzer on 2010-04-29
Any help on this?

---

