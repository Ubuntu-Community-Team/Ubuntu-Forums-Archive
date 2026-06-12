---
title: "virtualbox 2.1.2 grub error"
date: 2009-02-12
forum: Virtualisation
---

### Post by OSX@Linux on 2009-02-12
I read in the Virtualbox guide that one could use virtualbox to boot a virtual machine from a hard disk partition. I've followed all of the instructions, but Grub keeps popping up with "ERROR 17". The hard disk is split up into 1 NTFS Partition, 2 EXT3 Partitions and a swap partition. Any Help Much Appreciated:

---

### Post by dcstar on 2009-02-12
> **OSX@Linux said:**
> I read in the Virtualbox guide that one could use virtualbox to boot a virtual machine from a hard disk partition. I've followed all of the instructions, but Grub keeps popping up with "ERROR 17". The hard disk is split up into 1 NTFS Partition, 2 EXT3 Partitions and a swap partition. Any Help Much Appreciated:

There is a Virtualization forum for all VM questions.

---

### Post by OSX@Linux on 2009-02-12
Sorry, i'm new here. Thanks. I'll post there. Where is the virtualization forum. Can't find it

---

### Post by caljohnsmith on 2009-02-12
How about posting:
```
sudo fdisk -lu
```
And also post the menu.lst in the Grub ISO that you created in order to boot a partition from your HDD. And lastly, which OS are you trying to boot, and what partition is on?

---

### Post by OSX@Linux on 2009-02-12
Never mind. Here's the url of the thread

[http://ubuntuforums.org/showthread.php?t=1068397](http://ubuntuforums.org/showthread.php?t=1068397)

---

### Post by OSX@Linux on 2009-02-12
It's a NTFS File System with Windows XP Professional on it. Located on Partition 1.


# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=521a6c78-9de8-4552-8eb9-f460d455d107 ro

[ATTACH]103118[/ATTACH]

---

### Post by dmizer on 2009-02-12
No worries, but next time, use the report post button: [img]http://ubuntuforums.org/images/buttons/report.gif[/img], and indicate that you'd like your thread moved. It's a lot less work for us to move an existing thread than it is to close a duplicate and merge posts.

Thanks! :)

---

### Post by OSX@Linux on 2009-02-12
My Bad. I didn't see the Virtualization category in the forum jump menu.

---

