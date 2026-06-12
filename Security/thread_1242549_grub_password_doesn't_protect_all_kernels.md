---
title: "grub password doesn't protect all kernels"
date: 2009-08-17
forum: Security
---

### Post by emkersyt on 2009-08-17
Hi, I try to understand the following issue:

I had previously a Debian installed, later I put an Ubuntu distribution on the same drive.
The Ubuntu installer updated my grub configuration. Now I want all single-user kernels to be protected by a grub password.
It works all fine with the Ubuntu ones, but the Debian entries are just ignored by the password mechanism and would start up without password. As you will see these kernels own the password line the same way the Ubuntu entries do.
After a few tests I am guessing that grub always uses the config file on the Ubuntu partition whether it is booting into Debian (which has its own /boot/grub/menu.lst - unused apparently) or Ubuntu. Ubuntu is installed on /dev/hda1 and Debian is on /dev/hda2.

I post my /boot/grub/menu.lst:

```
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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

password --md5	$1$MpETA/$Tr.IQBJ6wte/95.mQOLFz.

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
# kopt=root=UUID=414cda20-124f-4479-bd23-f75fc612f78e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=414cda20-124f-4479-bd23-f75fc612f78e

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=true

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##


title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		414cda20-124f-4479-bd23-f75fc612f78e
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=414cda20-124f-4479-bd23-f75fc612f78e ro
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		414cda20-124f-4479-bd23-f75fc612f78e
lock
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=414cda20-124f-4479-bd23-f75fc612f78e ro  single
initrd		/boot/initrd.img-2.6.28-14-generic
password --md5	$1$MpETA/$Tr.IQBJ6wte/95.mQOLFz.

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		414cda20-124f-4479-bd23-f75fc612f78e
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=414cda20-124f-4479-bd23-f75fc612f78e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		414cda20-124f-4479-bd23-f75fc612f78e
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=414cda20-124f-4479-bd23-f75fc612f78e ro  single
initrd		/boot/initrd.img-2.6.28-13-generic
password --md5	$1$MpETA/$Tr.IQBJ6wte/95.mQOLFz.

title		Ubuntu 9.04, kernel 2.6.28-3-rt
uuid		414cda20-124f-4479-bd23-f75fc612f78e
kernel		/boot/vmlinuz-2.6.28-3-rt root=UUID=414cda20-124f-4479-bd23-f75fc612f78e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-3-rt
quiet

title		Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode)
uuid		414cda20-124f-4479-bd23-f75fc612f78e
kernel		/boot/vmlinuz-2.6.28-3-rt root=UUID=414cda20-124f-4479-bd23-f75fc612f78e ro  single
initrd		/boot/initrd.img-2.6.28-3-rt
password --md5	$1$MpETA/$Tr.IQBJ6wte/95.mQOLFz.

title		Ubuntu 9.04, memtest86+
uuid		414cda20-124f-4479-bd23-f75fc612f78e
kernel		/boot/memtest86+.bin
quiet

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Debian GNU/Linux, kernel 2.6.26-2-686 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.26-2-686 root=/dev/sda2 ro quiet 
initrd		/boot/initrd.img-2.6.26-2-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Debian GNU/Linux, kernel 2.6.26-2-686 (single-user mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.26-2-686 root=/dev/sda2 ro single 
initrd		/boot/initrd.img-2.6.26-2-686
savedefault
boot
password --md5	$1$MpETA/$Tr.IQBJ6wte/95.mQOLFz.


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Debian GNU/Linux, kernel 2.6.26-1-686 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.26-1-686 root=/dev/sda2 ro quiet 
initrd		/boot/initrd.img-2.6.26-1-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Debian GNU/Linux, kernel 2.6.26-1-686 (single-user mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.26-1-686 root=/dev/sda2 ro single 
initrd		/boot/initrd.img-2.6.26-1-686
savedefault
boot
password --md5	$1$MpETA/$Tr.IQBJ6wte/95.mQOLFz.
### END DEBIAN AUTOMAGIC KERNELS LIST
```

Note that i moved the last entry (### END DEBIAN AUTOMAGIC KERNEL LIST) from its original position (after the divider between Ubuntu and Debian) to the end because I thought that this way it would be including the Debian kernels also. It doesn't seem to make any difference.

I suspect the problem could have to do with that line "default grub root device". Maybe I have to tell the Debian system that it has to look for its grub configuration on the Ubuntu partition. Any ideas?

---

### Post by Bachstelze on 2009-08-17
If you want to protect all entries, your password should be at the beginning of your config file.

---

### Post by emkersyt on 2009-08-17
You probably mean that the password should be defined in the general section before the ### BEGIN AUTOMAGIC KERNELS LIST line. That is how they explain it in the howtos and that is what I did also:

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

password --md5	$1$MpETA/$Tr.IQBJ6wte/95.mQOLFz.

### BEGIN AUTOMAGIC KERNELS LIST

It does protect the editing mode but not the Debian kernels. Did you refer to any other place?

---

### Post by koenn on 2009-08-19
> ## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and[B] entries protected by the
# command 'lock'[/B]

means you have to lock the entries that you want to password-protect, eg

```
title		Debian GNU/Linux, kernel 2.6.26-1-686 (single-user mode) (on /dev/sda2)
lock
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.26-1-686 root=/dev/sda2 ro single 
initrd		/boot/initrd.img-2.6.26-1-686
savedefault
boot
```

(part of) this can be automated by setting the lock options to true, eg
```
# lockold=true
```
& run update-grub to re-generate a new  menu.list.

---

### Post by emkersyt on 2009-08-21
Thanks for your comments!

I did lock the entries I wanted to protect as you can see in my first post. I tried both variants: locking with the word "lock" as koenn describes and also by putting the whole password hash into the entry. I kept the latter because the only difference is that it doesn't come up with an error message when I try to boot the protected kernel but asks me for the password right away. That is with the Ubuntu kernels.

Unfortunately the Debian kernels are still ignored by the password mechanism. I tried once again putting the "lock" entry and executing "update-grub" after editing but it doesn't change anything. 
After a few tests I know for sure now that all kernel use exclusively the Ubuntu partition menu.lst. So the problem can't be the menu.lst on the Debian partition. 

Btw, I changed also the lockold option to "true".

Anyone can make suggestions how to set up a host-wide grub config which applies the same rules to all system entries? Anyone has observed the same behavior with his or her multi-boot grub setup?

---

