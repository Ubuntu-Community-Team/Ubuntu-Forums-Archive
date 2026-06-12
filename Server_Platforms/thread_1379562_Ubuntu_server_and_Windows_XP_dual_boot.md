---
title: "Ubuntu server and Windows XP dual boot"
date: 2010-01-12
forum: Server Platforms
---

### Post by weky on 2010-01-12
I have problem with booting into xp. First I installed Ubuntu server then XP.

That machine has two hdd and this is otput of fdisk -l command
```
Disk /dev/sda: 2040 MB, 2040643584 bytes
255 heads, 63 sectors/track, 248 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         229     1839411   83  Linux
/dev/sda2             230         248      152617+   5  Extended
/dev/sda5             230         248      152586   82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00096154

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14372   115443058+  83  Linux
/dev/sdb2   *       14373       14945     4602622+   7  HPFS/NTFS

```

And menu.lst file looks like this:
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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
title		Windows 95/98/NT/2000
root		(hd1,1)
makeactive
chainloader	+1

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
# kopt=root=UUID=370038a5-cf39-4ec6-9132-7c624efb102c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=370038a5-cf39-4ec6-9132-7c624efb102c

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		370038a5-cf39-4ec6-9132-7c624efb102c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=370038a5-cf39-4ec6-9132-7c624efb102c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		370038a5-cf39-4ec6-9132-7c624efb102c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=370038a5-cf39-4ec6-9132-7c624efb102c ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		370038a5-cf39-4ec6-9132-7c624efb102c
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

```

when I want to boot into xp I get some errors from grub and need to reboot... please help me

---

### Post by tlcook on 2010-01-12
Have you tried installing XP first, then Ubuntu Server? I thought it worked better that way round (did for me).

---

### Post by oldfred on 2010-01-12
Try this entry, if this does not work we will need the entire boot info script of your system. Or your windows has boot issues of its own.


# on /dev/sdb2
title        Microsoft Windows XP Professional
rootnoverify    (hd1,1)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

---

### Post by R.Bucky on 2010-01-12
Windows really needs to be the first machine on the hdd. It protests otherwise, as you have figured out.

---

### Post by weky on 2010-01-13
> **oldfred said:**
> Try this entry, if this does not work we will need the entire boot info script of your system. Or your windows has boot issues of its own.


# on /dev/sdb2
title        Microsoft Windows XP Professional
rootnoverify    (hd1,1)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

This solution worked for me. Thanks!

---

