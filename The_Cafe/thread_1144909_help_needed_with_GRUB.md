---
title: "help needed with GRUB"
date: 2009-05-01
forum: The Cafe
---

### Post by SpriteSODA on 2009-05-01
Hi guys,
I'm using Ubuntu 9.04 and yesterday i installed Arch Linux on a different drive. My problem is that I can't seem to configure grub right, so when I attempt to boot to Arch it says: "Error 17: Unable to mount partition" or something like that. my menu.lst file:

```

default 0
timeout 10

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
# kopt=root=UUID=c0f42436-001a-42ac-a496-15d414fccef4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c0f42436-001a-42ac-a496-15d414fccef4

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

title Ubuntu 9.04, kernel 2.6.28-11-generic
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=c0f42436-001a-42ac-a496-15d414fccef4 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=c0f42436-001a-42ac-a496-15d414fccef4 ro  single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, kernel 2.6.27-11-generic
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=c0f42436-001a-42ac-a496-15d414fccef4 ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=c0f42436-001a-42ac-a496-15d414fccef4 ro  single
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 9.04, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Microsoft Windows XP Professional
root (hd1,0)
chainloader +1
savedefault
makeactive

# (0) Arch Linux
title Arch Linux
root (hd0,0)
kernel /boot/vmlinuz26 root=UUID=7383920f-9943-4dea-b02e-c5dd1e34612e ro
initrd /boot/kernel26.img
 
# (1) Arch Linux Fallback
title Arch Linux Fallback
root (hd0,0)
kernel /boot/vmlinuz26 root=UUID=7383920f-9943-4dea-b02e-c5dd1e34612e ro
initrd /boot/kernel26-fallback.img

```

Ubuntu is on sdb7 and Arch is on sda1.

---

### Post by Eisenwinter on 2009-05-01
Why would you even want to have Ubuntu installed, when you have Arch installed?

But now, seriously:

Error 17 claims that the partition that you're attempting to boot is of a format that GRUB does not recognize.

Make certain that:
-The GRUB configuration file points to the correct device AND partition.
-Make certain that the partition on the device is formatted and of a format that GRUB can read (such as EXT3).

You can read about it in [http://www.gnu.org/software/grub/manual/html_node/](http://www.gnu.org/software/grub/manual/html_node/)

EDIT V2.0:

From the GRUB manual, error messages section:
17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

---

### Post by dragos240 on 2009-05-01
look at the device.map

---

### Post by SpriteSODA on 2009-05-01
this is totally weird. I installed it as ext3, as i can see in gparted :
[http://razup.co.il/imgs/91241182561.png](http://razup.co.il/imgs/91241182561.png)

but in fdisk -l it is something else:
[http://razup.co.il/imgs/411241182626.png](http://razup.co.il/imgs/411241182626.png)

any idea what the fudge?

---

### Post by Eisenwinter on 2009-05-01
It seems like everything is alright, except that GRUB doesn't recognize the file system.

Are you trying to boot from Ext4? GRUB on its own **cannot** boot Ext4 partitions.

Though, if you used the 2009.02 Arch installer, boot into it, and choose to install GRUB **from the disc**.

You have a Tools option in the menu (I think that's where it's at), go there and select "Install grub boot loader on hd(x,x)".

You should now be able to boot Ext4.

The alternative is to revert back to Ext3, of course, but I don't see why you would want to go through the entire installation process again.

---

### Post by SpriteSODA on 2009-05-01
nope, there is no ext4 in play, everything is ext3 :S

---

### Post by Eisenwinter on 2009-05-01
> **SpriteSODA said:**
> this is totally weird. I installed it as ext3, as i can see in gparted :
[http://razup.co.il/imgs/91241182561.png](http://razup.co.il/imgs/91241182561.png)

but in fdisk -l it is something else:
[http://razup.co.il/imgs/411241182626.png](http://razup.co.il/imgs/411241182626.png)

any idea what the fudge?

Hm, that's very strange indeed.

I remember when I created an Ext4 FS on one of my disks, and in fdisk -l, it was shown as FAT16 (What the hell?)

I'm clueless as to why this happens.

But regardless, GRUB **can** boot NTFS (obviously).

It seems the partition creation process was somehow messed up.

In the Arch installer, did you use cFdisk to create the partition types? If not, use it next time, just to be sure the defined FS type is correct.

---

### Post by SpriteSODA on 2009-05-01
Actually it isn't really vanilla Arch, I installed Chackra via a live cd.

---

### Post by Eisenwinter on 2009-05-01
Oh, I have never installed, or used, Chakra.

How is the partitions setup done there? Give me more info on that, and I may be able to help you.

---

### Post by SpriteSODA on 2009-05-01
Hmm, I looked in the /boot/grub/ folder in sda1 (Arch's partition), this is the menu.lst the installation process created:
```

# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution 

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
#
#-*


# (1) Windows
 
# (0) Arch Linux
title Arch Linux
root (hd0,0)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/7383920f-9943-4dea-b02e-c5dd1e34612e ro
initrd /boot/kernel26.img
 
# (1) Arch Linux Fallback
title Arch Linux Fallback
root (hd0,0)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/7383920f-9943-4dea-b02e-c5dd1e34612e ro
initrd /boot/kernel26-fallback.img

```

I tried before with these values and still failed to boot there, but maybe it can teach us something?

BTW thanks alot for the help so far :)

---

### Post by Eisenwinter on 2009-05-01
I personally, don't like using UUIDs in GRUB's menu.lst.

You see the line saying "kernel /boot/X root=/dev/disk/..."?

Change /dev/disk/X to /dev/sda1 - see if it works.

---

### Post by SpriteSODA on 2009-05-01
Already attempted it and it didnt help :(

---

### Post by Eisenwinter on 2009-05-01
Ok, well.

From the screenshot of fdisk -l you posted, it says that partition type is NTFS/HPFS

EDIT after verifying the following action will NOT cause the data to be deleted: (this is for future reference, should anyone need it)

Go into cfdisk in Ubuntu (or wherever), and change the partition type for /dev/sda1 to **83**

83 is a Linux partition type.
82 is Linux swap.

Try to boot then.

---

### Post by SpriteSODA on 2009-05-01
ok, i dont really care if it'll delete it :P

---

### Post by Eisenwinter on 2009-05-01
ok, then try it and report results

---

### Post by SpriteSODA on 2009-05-01
It worked :D

Didn't even loose the data.
Thanks alot mate:)

---

### Post by Eisenwinter on 2009-05-01
You're welcome, glad it worked.

This just shows you how picky GRUB can be :P

---

### Post by SpriteSODA on 2009-05-01
no kidding :D

---

