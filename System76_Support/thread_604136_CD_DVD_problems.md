---
title: "CD DVD problems"
date: 2007-11-05
forum: System76 Support
---

### Post by led_scorched on 2007-11-05
I can't get my DVD drive to work.  Been trying to back up my files, and instead, K3B claims i have no drive to write to.  i went checked it out, and when i tried to mount the drive got this instead "mount: special device /dev/scd0 does not exist"

I'm running 7.10 on a gazelle.  Machine is about a month old.

---

### Post by thomasaaron on 2007-11-06
We've seen this problem recently on computers that have upgraded from Feisty to Gutsy via Update Manager.

Previously, this was only fixable via a re-install, but another customer may have figured out another way. Post the output of...

cat /boot/grub/menu.lst

We can try out his idea to see if it works. If it does not, I can send you re-install instructions that should fix it.

---

### Post by led_scorched on 2007-11-06
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# kopt=root=/dev/mapper/ubuntu-root ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-generic root=/dev/mapper/ubuntu-root ro quiet splash
initrd          /initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-generic root=/dev/mapper/ubuntu-root ro single
initrd          /initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.20-16-generic root=/dev/mapper/ubuntu-root ro quiet splash
initrd          /initrd.img-2.6.20-16-generic
quiet

title           Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.20-16-generic root=/dev/mapper/ubuntu-root ro single
initrd          /initrd.img-2.6.20-16-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by thomasaaron on 2007-11-06
Nope. That idea won't work on your set-up.

Instructions are here:
[http://system76.com/forums/viewtopic.php?t=4552&highlight=reinstall](http://system76.com/forums/viewtopic.php?t=4552&highlight=reinstall)

---

### Post by led_scorched on 2007-11-06
so am i screwed on getting my data, with out an external harddrive or something?

---

### Post by thomasaaron on 2007-11-06
Try the tips on this thread:

[http://ubuntuforums.org/showthread.php?t=580745](http://ubuntuforums.org/showthread.php?t=580745)

It might get your drive working long enough to retrieve your data.

---

### Post by TeagueSterling on 2007-11-09
I had this same problem, I was able to temporarily fix it by dropping back to the 2.6.20-16 kernel, so it may be a problem with the new kernel in gutsy.

I read somewhere that it may be tied to SATA support not being enabled in the 2.6.22-14 kernel, but I don't know enough myself to confirm or deny that.

---

