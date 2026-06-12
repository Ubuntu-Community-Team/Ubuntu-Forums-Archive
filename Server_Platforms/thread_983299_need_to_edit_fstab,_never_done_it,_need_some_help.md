---
title: "need to edit fstab, never done it, need some help"
date: 2008-11-15
forum: Server Platforms
---

### Post by c.wilson on 2008-11-15
I got this message from my server provider,

> *Please note that the first kernel is not active. When you reboot your server it will hang on this error. I choose the second kernel. If you want this by default after a restart you can edit this in the fstab
(nano /etc/fstab)

I do want that as default,

This is what my fstab file looks like
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ddad87da-78ea-4208-927c-9f8b632b9650 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=bac3b0c2-0fd4-4f13-a522-4039914cec2c /boot           ext2    defaults        0       2
# /dev/sda2
UUID=0aa9a841-0171-441d-ae80-72ea5a3ea66e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

I really don't want to screw this up, can someone help me edit the correct line and what I need to edit it too?

---

### Post by cdtech on 2008-11-15
Your kernel boot order is located in the file /boot/grub/menu.lst and not the fstab file. If you want to boot using a different kernel you'll need to edit the menu.lst and there is a line that says default:
```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0
```
The default is the order of boot.

You could just hit the esc key and select which kernel you want to boot from.

Can you post the output of:
```
gedit /boot/grub/menu.lst
```

---

### Post by c.wilson on 2008-11-15
thanks for help, this is the output you requested
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
# kopt=root=UUID=ddad87da-78ea-4208-927c-9f8b632b9650 ro

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

title		Ubuntu, kernel 2.6.22-14-server
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-server root=UUID=ddad87da-78ea-4208-927c-9f8b632b9650 ro quiet splash
initrd		/initrd.img-2.6.22-14-server
quiet
savedefault

title		Ubuntu, kernel 2.6.22-14-server (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-server root=UUID=ddad87da-78ea-4208-927c-9f8b632b9650 ro single
initrd		/initrd.img-2.6.22-14-server

title		Ubuntu, kernel 2.6.20-16-server
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-server root=UUID=ddad87da-78ea-4208-927c-9f8b632b9650 ro quiet splash
initrd		/initrd.img-2.6.20-16-server
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-server (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-server root=UUID=ddad87da-78ea-4208-927c-9f8b632b9650 ro single
initrd		/initrd.img-2.6.20-16-server

title		Ubuntu, kernel 2.6.20-15-server
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-server root=UUID=ddad87da-78ea-4208-927c-9f8b632b9650 ro quiet splash
initrd		/initrd.img-2.6.20-15-server
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-server (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-server root=UUID=ddad87da-78ea-4208-927c-9f8b632b9650 ro single
initrd		/initrd.img-2.6.20-15-server

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by cdtech on 2008-11-15
Which kernel is it that you want to boot from?

---

### Post by c.wilson on 2008-11-15
The one that the host is refering to as the second one, .. sry I can't be of more help

---

### Post by c.wilson on 2008-11-15
it's actually the one that's running now, is there a way to get the output of the one I'm running now?

---

### Post by cdtech on 2008-11-15
I'm sorry, I don't understand what you mean by "the host". If you want to use the second one by default, just change the "default 0" to "default 2":
```
sudo gedit /boot/grub/menu.lst
```
And change the bold:
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
default		**2**

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
# kopt=root=UUID=ddad87da-78ea-4208-927c-9f8b632b9650 ro

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

title		Ubuntu, kernel 2.6.22-14-server
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-server root=UUID=ddad87da-78ea-4208-927c-9f8b632b9650 ro quiet splash
initrd		/initrd.img-2.6.22-14-server
quiet
**#** savedefault

title		Ubuntu, kernel 2.6.22-14-server (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-server root=UUID=ddad87da-78ea-4208-927c-9f8b632b9650 ro single
initrd		/initrd.img-2.6.22-14-server

title		Ubuntu, kernel 2.6.20-16-server
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-server root=UUID=ddad87da-78ea-4208-927c-9f8b632b9650 ro quiet splash
initrd		/initrd.img-2.6.20-16-server
quiet
**#** savedefault

title		Ubuntu, kernel 2.6.20-16-server (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-server root=UUID=ddad87da-78ea-4208-927c-9f8b632b9650 ro single
initrd		/initrd.img-2.6.20-16-server

title		Ubuntu, kernel 2.6.20-15-server
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-server root=UUID=ddad87da-78ea-4208-927c-9f8b632b9650 ro quiet splash
initrd		/initrd.img-2.6.20-15-server
quiet
**#** savedefault

title		Ubuntu, kernel 2.6.20-15-server (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-server root=UUID=ddad87da-78ea-4208-927c-9f8b632b9650 ro single
initrd		/initrd.img-2.6.20-15-server

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```
And comment the "savedefault" as I did.

---

### Post by cdtech on 2008-11-15
> **c.wilson said:**
> it's actually the one that's running now, is there a way to get the output of the one I'm running now?

Type in a terminal:
```
uname -r
```

---

### Post by c.wilson on 2008-11-15
I just ment my hosting provider for the server, I have an unmanged box, so he was just giving me a heads up when he reboted the machine.

---

### Post by c.wilson on 2008-11-15
ok the uname command gave me this

```
2.6.20-16-server
```

---

### Post by cdtech on 2008-11-15
> **c.wilson said:**
> ok the uname command gave me this

```
2.6.20-16-server
```

Ok, so changing the default to 2 and comment out the "savedefault" will work for you. Linux counts from "0" so the kernel entries you have start from "0". The "1" selection would be the "Ubuntu, kernel 2.6.22-14-server (recovery mode)" and the "2" would be the "Ubuntu, kernel 2.6.20-16-server" entry.

---

### Post by c.wilson on 2008-11-15
ok so I can just copy and paste the one you edited a couple threads ago and be good?

---

### Post by cdtech on 2008-11-15
Sure, that'll work.....

---

### Post by c.wilson on 2008-11-15
Thanks man, your a life saver =)

---

