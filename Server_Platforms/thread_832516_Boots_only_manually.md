---
title: "Boots only manually"
date: 2008-06-17
forum: Server Platforms
---

### Post by mmcsherr on 2008-06-17
I have a weird problem.  I can only boot the system manually.  I have 5 drives, device.map listed below, first 3 are 1TB drives in raid 5 mode, the other as raid 1 hosting "/".  What happens when the system boots, it boot sto a grub prompt.

device.map files:
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
(hd3)   /dev/sdd
(hd4)   /dev/sde

I then enter the following commands to boot the system:
root            (hd4,0)
kernel          /boot/vmlinuz-2.6.24-16-server root=/dev/md2 ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-server
boot

The system then boots into ubuntu server 8.0.4 LTS 64-bit.  If I do a FIND /boot/vmlinuz... it finds it on hd0 and on hd4.  I had Fedora 9 64-bit on there before. I have tried a lot of combinations in the menu.lst file, shown below:
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/md2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd4,0)

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

title           Ubuntu 8.04, kernel 2.6.24-16-server
root            (hd4,0)
kernel          /boot/vmlinuz-2.6.24-16-server root=/dev/md2 ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-server
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-server (recovery mode)
root            (hd4,0)
kernel          /boot/vmlinuz-2.6.24-16-server root=/dev/md2 ro single
initrd          /boot/initrd.img-2.6.24-16-server

title           Ubuntu 8.04, memtest86+
root            (hd4,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
I am not sure what to do next, I hate to manually boot evertime I need to boot the system or on a power failure.  HELP anyone!  Is it theat there is grub on 2 disks?  If so, how do I get rid of it off of one of them?

---

### Post by windependence on 2008-06-17
I would highly recommend creating a non-RAID boot partition (256 MB is fine) and load grub on that partition. Booting from a RAID partition is not recommended.

-Tim

---

### Post by mmcsherr on 2008-06-18
Talking about disks, boot directories and all, I am not a linux/unix guru by no means, what is the ideal layout for my system given that I have 3 1TB drives on 1 sata controller and 2 250GB drive another.  The purpose of the system is to host web server apps I develop and as a file server for my home network.  Also, I was planning on using some of the TBs for backup for my other systems as well.  Thanks in advance for suggestions.

---

