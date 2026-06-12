---
title: "slackware grub boot failed"
date: 2007-08-05
forum: Slackware and derivatives
---

### Post by eier on 2007-08-05
hi.

i've just installed slackware 12 on my computer.
i have ubuntu installed too, and i want to use grub to load slackware.
i've added it to grub,when i start it it loads lots of things and then it stops and then gives me an error,something like root sda4 not valid device select correct root partition. (I don't remember the exact words.
here's my menu.lst
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

gfxmenu /boot/grub/message.ububrown

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=c8e3ea52-2364-4e6e-94b5-a8c9f48cb847 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title Slackware 12, kernel 2.6.21.5-huge
root (hd0,3)
kernel /boot/vmlinuz-huge-2.6.21.5 root=/dev/sda4 ro
boot

title		(K)(X)ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c8e3ea52-2364-4e6e-94b5-a8c9f48cb847 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
boot


### END DEBIAN AUTOMAGIC KERNELS LIST

```

and here's my fdisk -l

```
Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            6480       14334    63095287+  83  Linux (ubuntu)
/dev/sda3           14335       14946     4915890    5  Extended
/dev/sda4            3825        6479    21326287+  83  Linux (slackware)
/dev/sda5           14335       14946     4915858+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38912   312560608+   c  W95 FAT32 (LBA) (external disk)

```

anyone know a solution?

---

### Post by johnny4north on 2007-08-06
Slackware installs LILO as default, but GRUB can be installed w/ some work.  here is a link to a howto - [http://humanreadable.nfshost.com/sdeg/grub.htm](http://humanreadable.nfshost.com/sdeg/grub.htm) good luck

---

### Post by eier on 2007-08-06
yes, but i skipped those steps when i installed slackware beceause i've alredy have grub on my system. my problem is putting a slackware entry to my menu.lst

---

### Post by johnny4north on 2007-08-06
i can see that you have done some editing to the menu.lst file so im guessing that you can boot into ubuntu, and have done all the good things like back up your original menu.lst. Use gedit to edit the menu.lst file.  Do not use a open office or other. Boot in to ubuntu then, start the terminal and use the command below.
> sudo gedit /boot/grub/menu.lst

this is a copy of the end of your menu.lst
> ## ## End Default Options ##

title Slackware 12, kernel 2.6.21.5-huge
root (hd0,3)
kernel /boot/vmlinuz-huge-2.6.21.5 root=/dev/sda4 ro
boot

title		(K)(X)ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c8e3ea52-2364-4e6e-94b5-a8c9f48cb847 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
boot


### END DEBIAN AUTOMAGIC KERNELS LIST

i would recommend moving ubuntu up to default spot. and add "savedefault".  check for typos and errors carefully then save file.  recommended editing of end of menu.lst file shown below
> ## ## End Default Options ##

title		(K)(X)ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c8e3ea52-2364-4e6e-94b5-a8c9f48cb847 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot

###corrected solution thanks Confused57

title Slackware 12, kernel 2.6.21.5-huge
root (hd0,3)
kernel /boot/vmlinuz-huge-2.6.21.5 root=/dev/hda4 ro
boot


### END DEBIAN AUTOMAGIC KERNELS LIST
here are helpful links -
[https://help.ubuntu.com/7.04/installation-guide/i386/rescue.html](https://help.ubuntu.com/7.04/installation-guide/i386/rescue.html)
[http://www.brunolinux.com/05-Configuring_Your_System/Multiboot_grub.html](http://www.brunolinux.com/05-Configuring_Your_System/Multiboot_grub.html)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Grub](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Grub)
please read and research the grub, the three sites above would be the min, info i would learn before proceeding with editing your menu.lst file.  i believe when you originally install the ubuntu the grub was installed to the master boot record(mbr).  all other distros and windows should be installed to the root, then adding the "chainloader +1" for slackware and windows. Note- windows defaults installs to mbr, so install 1st., then ubuntu, finally slackware.  people please double check, including myself.  thanks confuse57 for catching that one.

---

### Post by confused57 on 2007-08-06
If you have an IDE drive, then try /dev/hda4:
```
title Slackware 12, kernel 2.6.21.5-huge
root (hd0,3)
kernel /boot/vmlinuz-huge-2.6.21.5 root=/dev/hda4 ro
boot
```

---

### Post by eier on 2007-08-07
Thanks for your'e help guys.
It works now.

here's my slackware entry in menu.lst
```
title Slackware 12, kernel 2.6.21.5-huge
root (hd0,3)
kernel /boot/vmlinuz-huge-2.6.21.5 root=/dev/hda4 ro
boot
```

ubuntu read my disk as sda and slackware reads it as hda, don't know why.

---

### Post by mrintegrity on 2007-11-23
the reason ubuntu sees your disk as sd instead of hd is that it is either SATA or SCSI and using some generic IDE kernel module for disk access will be really ineficient.. in slackware you need to check your kernel configuration for SCSI or SATA support, if it's a modern desktop computer then it will certainly be SATA (note that if you fix the kernel then you will also NEED to put the grub entry back to sda instead of hda!)

Alan

---

### Post by bonzodog on 2007-11-23
No, IDE drives are now seen as SATA as well, with recent kernels. 
It's a module called libata, which they have obviously decided not to turn on in Slackware.

---

