---
title: "VirtualBox OSE usb for"
date: 2008-03-05
forum: Virtualisation
---

### Post by samtrevino on 2008-03-05
O.K. I'm by no one's imagination a Linux expert, but I do know a few things so please help me solve this issue. 

First what am I attempting to do here? I am attempting to run a Windows XP Virtualization and connect that to my T-Mobile 8320 Curve and use it as a modem to connect to the Internet anywhere. I've tried this in Linux, using my 8320 as a modem, no joy.  I want to try this via Virtualization to see if it can be done within a virtualization.

I've loaded VirtualBox OSE on a Gusty Gibbon 7.10 platform am currently running XP in virtualization. 

I do not have access to USB devices. Please understand I am seeking a solution with OSE as I prefer open source and well no cost. 

Also I understand that others have accomplished getting access to USB in VirtualBox OSE if I read other forums correctly. 

Below is a copy of my /etc/init.d/mountdevsubfs.sh file:

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
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs ",devgid=1000" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0664,listmode=0644
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




Also /etc/udev/rules.d/40-permissions.rules file:


# This file establishes permissions and ownership of devices according
# to Ubuntu policy.  See udev(7) for syntax.
#
# The names of the devices must not be set here, but in 20-names.rules;
# user-friendly symlinks (which need no permissions or ownership) should
# be set in 60-symlinks.rules.

# Block devices
SUBSYSTEM!="block", GOTO="block_end"
ATTRS{removable}!="1",			GROUP="disk"
ATTRS{removable}=="1",			GROUP="floppy"
SUBSYSTEMS=="usb",			GROUP="plugdev"
SUBSYSTEMS=="ieee1394",			GROUP="plugdev"
SUBSYSTEMS=="mmc",			GROUP="plugdev"
SUBSYSTEMS=="pcmcia",			GROUP="plugdev"
LABEL="block_end"

# IDE devices
ENV{ID_CDROM}=="?*",			GROUP="cdrom"
KERNEL=="ht[0-9]*",			GROUP="tape"
KERNEL=="nht[0-9]*",			GROUP="tape"

# IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
# device on the bus and those devices may do anything as root on your system.
# Yes, I know it also happens to be the only way to rewind your video camera,
# but it's not going to be group "video", okay?
KERNEL=="raw1394",			GROUP="disk"
KERNEL=="dv1394*",			GROUP="video"
KERNEL=="video1394*",			GROUP="video"

# Packet CD devices, group under /dev/pktcdvd
KERNEL=="pktcdvd",			MODE="0644"
KERNEL=="pktcdvd[0-9]*",		GROUP="cdrom"

# Printers and Parallel devices
SUBSYSTEM=="printer",			GROUP="lp"
SUBSYSTEM=="ppdev",			GROUP="lp"
SUBSYSTEM=="usb", KERNEL=="lp[0-9]*",	GROUP="lp"
KERNEL=="pt[0-9]*",			GROUP="tape"
KERNEL=="pht[0-9]*",			GROUP="tape"

# SCSI devices
SUBSYSTEMS=="scsi", GOTO="scsi_start"
GOTO="scsi_end"
LABEL="scsi_start"
ATTRS{type}=="1",			GROUP="tape"
ATTRS{type}=="5",			GROUP="cdrom"
ATTRS{type}=="6",			GROUP="scanner"
ATTRS{type}=="8",			GROUP="tape"
ATTRS{type}=="3", ATTRS{vendor}=="HP",	GROUP="scanner"
ATTRS{type}=="3", ATTRS{vendor}=="Epson", GROUP="scanner"
ATTRS{type}=="3", ATTRS{vendor}=="EPSON", GROUP="scanner"
LABEL="scsi_end"

# Serial devices
SUBSYSTEM=="tty",			GROUP="dialout"
SUBSYSTEM=="capi",			GROUP="dialout"
SUBSYSTEM=="slamr",			GROUP="dialout"
SUBSYSTEM=="zaptel",			GROUP="dialout"
KERNEL=="ttyLTM[0-9]*",			GROUP="dialout", MODE="0660"

# Sound devices
SUBSYSTEM=="sound",			GROUP="audio"

# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device", MODE="0664"

# vc (virtual console) devices
SUBSYSTEM!="tty", GOTO="vc_end"
KERNEL=="console",			GROUP="root", MODE="0600"
KERNEL=="ptmx",				GROUP="root", MODE="0666"
KERNEL=="pty*",				GROUP="tty", MODE="0666"
KERNEL=="tty",				GROUP="root", MODE="0666"
KERNEL=="tty[0-9]*",			GROUP="root"
KERNEL=="vcs*",				GROUP="root"
LABEL="vc_end"

# Video devices
SUBSYSTEM=="drm",			GROUP="video"
SUBSYSTEM=="dvb",			GROUP="video"
SUBSYSTEM=="graphics",			GROUP="video"
SUBSYSTEM=="video4linux",		GROUP="video"
KERNEL=="agpgart",			GROUP="video"
KERNEL=="nvidia*",			GROUP="video"

# Other devices, by name
KERNEL=="null",				MODE="0666"
KERNEL=="zero",				MODE="0666"
KERNEL=="full",				MODE="0666"
KERNEL=="random",			MODE="0666"
KERNEL=="urandom",			MODE="0666"
KERNEL=="mem",				GROUP="kmem", MODE="0640"
KERNEL=="kmem",				GROUP="kmem", MODE="0640"
KERNEL=="port",				GROUP="kmem", MODE="0640"
KERNEL=="nvram",			GROUP="nvram"
KERNEL=="rtc",				GROUP="audio"
KERNEL=="inotify",			MODE="0666"
KERNEL=="js[0-9]*",			GROUP="plugdev"
KERNEL=="vboxdrv",                      GROUP="vboxusers", MODE="0660"


Let me know if other information is required.

Thanks,

Sam


Edit:
[http://www.blog.arun-prabha.com/2007/10/26/usb-not-working-with-virtualbox-in-ubuntu-7-10-gutsy-gibbon/](http://www.blog.arun-prabha.com/2007/10/26/usb-not-working-with-virtualbox-in-ubuntu-7-10-gutsy-gibbon/)

[http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

[http://ubuntuforums.org/showthread.php?t=393582&highlight=VirtualBox+OSE+usb](http://ubuntuforums.org/showthread.php?t=393582&highlight=VirtualBox+OSE+usb)

[http://ubuntuforums.org/showthread.php?t=657191&highlight=VirtualBox+OSE+usb](http://ubuntuforums.org/showthread.php?t=657191&highlight=VirtualBox+OSE+usb)

I did a lot of what was recommended but nothing worked and I afraid I screwed something up.

Any help is appreciated.

---

### Post by ung/xunil on 2008-03-11
Hi samtrevino,

forget about USB in Virtualbox OSE (OSE is the Open Source Edition). From [VirtualBox own page]("http://www.virtualbox.org/wiki/Editions"):

> Closed-source features

The following list shows the enterprise features that are only present in the closed-source edition. [...]

    * USB support 

    VirtualBox implements a virtual USB controller and supports passing through USB 1.1 and USB 2.0 devices to virtual machines. [...]


You have to use the closed-source edition of Virtualbox binary/package from their website, not the OSE package from Ubuntu repositories, to be able to use USB. More about what to do after installing the closed-source package of VirtualBox look at this page: [https://help.ubuntu.com/community/VirtualBox]("https://help.ubuntu.com/community/VirtualBox")

Good luck.

---

### Post by imcgee on 2011-05-16
Gents, i also struggled with this one, open the user management and find the group for vboxusers (or similar) and add your user to the group.
then when you run your virtual machine go to the device menu and select the usb device.
 
worked for me plugging in an ipod
 
ubuntu 11.04
virtualbox ose

---

