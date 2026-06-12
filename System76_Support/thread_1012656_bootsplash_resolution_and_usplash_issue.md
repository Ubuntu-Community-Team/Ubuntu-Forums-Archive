---
title: "bootsplash resolution and usplash issue"
date: 2008-12-16
forum: System76 Support
---

### Post by Bllz on 2008-12-16
I bought a serval performance last year and it's working great.  However, since I reinstalled Ubuntu, I've been having some minor trouble with a few aesthetic annoyances.

My screen resolution is 1680x1050, which should be the vga=369 GRUB option.  I defined this option in my menu.lst (see below) but for some reason, everytime my serval boots, I get an error which reads something like "unrecognized video mode 171"  I tried using both decimal and hex form for the 369 value, but no can do... (sanity check:  369 = 0x171)

Am I missing something?  Do I have to somehow "reload" the menu.lst file like for sources.list?

Also, when my serval boots, my usplash logo's bar fills about a quarter of the way before text appears regarding the fsck filesystem check.  Is there a way to correct this?

Thanks a bunch!
Louis

Menu.lst:
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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
#password --md5 $1$vmAfp$UlejohU96guR0Y0NMS6xe.
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
# kopt=root=UUID=45fd18df-c76d-4208-a579-cf6b8023a00f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=45fd18df-c76d-4208-a579-cf6b8023a00f

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
# defoptions=quiet splash vga=369

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=true

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
# howmany=2


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

title		Ubuntu 8.10, kernel 2.6.27-10-generic
uuid		45fd18df-c76d-4208-a579-cf6b8023a00f
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=45fd18df-c76d-4208-a579-cf6b8023a00f ro quiet splash vga=369
initrd		/boot/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
lock
uuid		45fd18df-c76d-4208-a579-cf6b8023a00f
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=45fd18df-c76d-4208-a579-cf6b8023a00f ro  single
initrd		/boot/initrd.img-2.6.27-10-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
lock
uuid		45fd18df-c76d-4208-a579-cf6b8023a00f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=45fd18df-c76d-4208-a579-cf6b8023a00f ro quiet splash vga=369 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
lock
uuid		45fd18df-c76d-4208-a579-cf6b8023a00f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=45fd18df-c76d-4208-a579-cf6b8023a00f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		45fd18df-c76d-4208-a579-cf6b8023a00f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by thomasaaron on 2008-12-16
Is your resolution correct once you've logged in? Or are you just trying to straighten out the virtual terminal resolution?

Are you saying it runs the fsck every time you boot? Are you letting it complete? If you are, try mounting the drives and running fsck manually from a live CD.

---

### Post by Bllz on 2008-12-16
> **thomasaaron said:**
> Is your resolution correct once you've logged in? Or are you just trying to straighten out the virtual terminal resolution?

Are you saying it runs the fsck every time you boot? Are you letting it complete? If you are, try mounting the drives and running fsck manually from a live CD.

Tom,
Thanks for the quick reply (as usual!)

Once I'm logged in, the resolution is correct and everything works flawlessly.  I'm trying to get the boot splash (the ubuntu logo with the orange bar that fills up) to display at 1680x1050 (or any resolution that doesn't stretch it out).  I should add that when I get the error message, I can hit "enter" and pick from a list of supported video modes.  1680x1030x32 is right there at the bottom right, and when I type the number (369), it seems to work.  I just can't figure out why it doesn't work when defined in menu.lst 


As for fsck, yes, it runs every time I boot.  AFAIK, I am letting it complete... I don't see any obvious error messages, and I'm not aborting it manually.  I'll give the live CD a whirl and see how that turns out.  I'll post the results as an edit to this post.  I should also specify that I'm using a ReiserFS boot partition, in case that makes a difference.

Thanks again,
Louis


*** EDIT ***

I can't quite figure out how to run fsck.  I tried fsck.reiserfs --check sda1 but got no relevant output.  That said, when I boot, I see a line that says 'filesystem is clean'

---

### Post by thomasaaron on 2008-12-16
> ReiserFS boot partition
That might be the issue, but I'm not sure. Never messed with ReiserFS.

From a live CD, you would just mount the partition and run...

```
sudo fsck /dev/sdxx
``` #Or /dev/<whatever it has labeled your filesystem... Go to System > Admin > Partition Editor on the live CD to see how it is labeled.

---

### Post by MorphWVUtuba on 2008-12-16
Just a shot in the dark here...

Would "sudo update-initramfs -k all -u" be any help here?

---

### Post by thomasaaron on 2008-12-16
Good idea.

Bllz, can you try that?

---

### Post by Bllz on 2008-12-16
I tried rebuilding the boot image, and that didn't work.  It's not a huge deal... I'm just a perfectionist.


Out of curiosity:  when System76 ships its computers, do you get usplash to render at the appriate resolution by editing menu.lst, or is there another way to do it?

Thanks,
Louis

---

### Post by thomasaaron on 2008-12-16
We don't do anything at all to it.

---

### Post by compholio on 2008-12-17
usplash has trouble with any screen size that's not 3:4.  I think it has something to do with what framebuffer driver is used in the kernel.  The last time I played with it I decided to just give up and live with it.  Also, it's more than just changing the grub option - you also have to edit /etc/usplash.conf and then rebuild the boot image (sudo update-initramfs -u).

---

### Post by hzsirmar on 2008-12-19
[Shenzhen Chip Optech Co., Ltd](http://www.alilinks.com/manufactures/975/Shenzhen-Chip-Optech-Co-Ltd.htm)Shenzhen Chip Optech Co., Ltd is a Hi-tech company in Shenzhen China, which is engaged in research, Production and construction of LED display. We are not only a manufacturer but also an experienced L [http://www.alilinks.com/manufactures/975/Shenzhen-Chip-Optech-Co-Ltd.htm](http://www.alilinks.com/manufactures/975/Shenzhen-Chip-Optech-Co-Ltd.htm)

---

