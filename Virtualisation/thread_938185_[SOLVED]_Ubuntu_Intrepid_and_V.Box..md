---
title: "[SOLVED] Ubuntu Intrepid and V.Box."
date: 2008-10-04
forum: Virtualisation
---

### Post by Dyffo on 2008-10-04
I have just installed "Ubuntu Intrepid " on my virtual box to try out before going for the full install to replace Hardy Heron.The problem I have is installing Guest Additions. If I try to run by Autorun I get the error message that the program cannot be found. If I try to run manually I am told that the program must be run with Administrator privilidges.Any ideas how to get this package going !!

---

### Post by b0b138 on 2008-10-04
The "autorun" going off the autorun.inf which will try to run VBoxWindowsAdditions.exe. And as you can guess is the one for windows guest.

You need to run VBoxLinuxAdditions-xxx.run as root.

sudo /media/cdrom/./VBoxLinuxAdditions-x86.run

---

### Post by Jose Catre-Vandis on 2008-10-04
And make sure you are using Virtualbox v2.02 which has bugfixes to allow 8.10 beta to run virtualised

---

### Post by Dyffo on 2008-10-05
Hi Guys - thanks - I have got it ( V.B. 2.02 ) and done it ( Run Additions from root ) and now it ALL works !!!!. Have you tried 8.10 Beta - if so what do you think of it ??

---

### Post by b0b138 on 2008-10-05
You will probably want to check out this thread [http://ubuntuforums.org/showthread.php?t=926408](http://ubuntuforums.org/showthread.php?t=926408) ;)

---

### Post by kj6ythgfg on 2008-12-09
I get an error that says :no such file or directory.please help:KS

---

### Post by Dyffo on 2008-12-10
What operation are you trying to carry out that gives you this message ??

---

### Post by dharkus on 2008-12-12
i got the same but i got:
sudo: /media/cdrom.VBoxLinuxAdditions-x86.run: command not found
what should i do now - used the exact command above

---

### Post by Dyffo on 2008-12-12
Hi there- these configurations worked for me.Perhaps all you need to do is run the last line -sudo/etc/init.d/vboxdrv setup.

Download VirtualBox:
Use the following links to download VirtualBox according to your CPU architecture. If you don't know what this means, you'd probably just better go with the i386 pacakge.

i386:
[http://www.virtualbox.org/download/1...hardy_i386.deb](http://www.virtualbox.org/download/1...hardy_i386.deb)
AMD64
[http://www.virtualbox.org/download/1...ardy_amd64.deb](http://www.virtualbox.org/download/1...ardy_amd64.deb)

Note: The VirtualBox that you have in the Add/Remove Programs list is different because it is the Open Source Edition. This is generally more difficult to configure, so use the normal VirtualBox program found in the link above.

Install VirtualBox:
Double-click on the package you just downloaded and you will be prompted to install it.

Setup Permissions:
This can be done in two different ways. The graphical way or the command line way.

Via Command Line:

[In Terminal]
Code:

sudo usermod -G vboxusers -a username

Via Graphical Menus:

Goto System -> Administration -> Users and Groups.

Click on the "Unlock" button and then enter in your password.

Click on the "Manage Groups" button.

Find the "vboxusers" group which is probably at the very bottom of the list, highlight it by clicking again, and click once more on "Properties".

Make sure there's a check mark next to your user's name, and you're finished.

Setup USB:
USB is disabled by default, so you'll probably want to enable it. Otherwise you'll get an error when you go into the "Settings" of your virtual machine. To correct this, you'll need to edit the mountdevsubfs.sh file:

[In Terminal]
Code:

sudo gedit /etc/init.d/mountdevsubfs.sh

Inside, you'll see a block of code that looks like this:

    #
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount --rbind /dev/bus/usb /proc/bus/usb

Change it to look like this (uncomment out the region by deleting the "#'s"):

    #
    # Magic to make /proc/bus/usb work
    #
    mkdir -p /dev/bus/usb/.usbfs
    domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    ln -s .usbfs/devices /dev/bus/usb/devices
    mount --rbind /dev/bus/usb /proc/bus/usb

Save the changes, log out, and then log back in again for the changes to take place.

Other:
The VirtualBox Guest Additions image (.iso) file is located here:
[http://www.virtualbox.org/download/1...ions_1.5.6.iso](http://www.virtualbox.org/download/1...ions_1.5.6.iso)

Minor Troubleshooting:
With these instructions, I was able to get my virtual machine working perfectly in VirtualBox. If you have any problems, please let me know by commenting below. I will help to resolve your issue and then place it with the solution in this section of the tutorial. Thank you.

Package Dependencies
If you run across a problem with dependencies (like libxercese27 which is included in the libxalan110 package), you'll have at this point to either install it first or go ahead with the installation and run "sudo apt-get -f install" to correct the problems.
Thanks Princey

Compilation of the kernel module FAILED! Error
While trying to install VirtualBox you receive an error like this:
Code:

"Compilation of the kernel module FAILED!

VirtualBox will not start until this problem is fixed. Please consult '/var/log/vbox-install.log' to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them and execute '/etc/init.d/vboxdrv' setup as root."

Run the command "sudo /etc/init.d/vboxdrv setup" and see if that helps. Again it worked for me. GOOD LUCK

---

### Post by gisham on 2008-12-13
***Please disregard, I found what I was looking for on one of my laptops.***

Dyffo,

I was following your instructions, but when I came to the part about modding the mountdevsubfs.sh file, I don't appear to have the section that you describe:
[INDENT]#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb[/INDENT]

Where would I insert this in the file? The contents of my file are:

[INDENT]#! /bin/sh
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
esac[/INDENT]

Thanks!

gisham

---

### Post by Dyffo on 2008-12-13
Hi Gisham,
This is a new error for me ! I can only suggest two things . Firtsly go to Synaptic in the System menu and check that - sh tool  - is installed, if in the search box you paste  - mountdevsubfs.sh - , this should bring it up.The other suggestion is that if this is a dependancy problem then in the terminal enter -
  sudo apt-get -f install .
At the moment can't think of any thing else, apart from TOTALLY uninstall V.Box thro Synaptic and start all over again.Alternativley thro' the terminal enter - 
 sudo apt-get remove--purge virtualbox
If none of this works, at the moment I am at a loss as to how to help, please keep me posted I welcome the feedback

---

### Post by gisham on 2008-12-14
Thanks for the assist, Dyffo. You were correct, sh-tools were not installed. Just before you replied, I just pasted your uncommented code into mountdevsubfs.sh in the same section place where it occured on my laptop.

gisham

---

