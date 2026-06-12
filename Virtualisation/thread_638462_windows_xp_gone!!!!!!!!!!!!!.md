---
title: "windows xp gone!!!!!!!!!!!!!"
date: 2007-12-12
forum: Virtualisation
---

### Post by Julius1988 on 2007-12-12
Hi,
I have been using windows for few years then i saw ubuntu & it was cool so i installed in my system but seems like i have lost my windows xp.This is bad guys,This is not the way i wanted it to be,is there any way to recover my windows without using:(recovery console of windows xp,this system had preinstalled xp in it so i dont have the cd)
Here is some description that should help u to identify my problem

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc164c164

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38912   312560608+   f  W95 Ext'd (LBA)
/dev/sda5            3825       10198    51199123+   7  HPFS/NTFS
/dev/sda6           10199       16572    51199123+   7  HPFS/NTFS
/dev/sda7           16573       22946    51199123+   7  HPFS/NTFS
/dev/sda8           22947       29320    51199123+   7  HPFS/NTFS
/dev/sda9           29321       38912    77047708+   7  HPFS/NTFS
/dev/sda10              1        3550    28515280+  83  Linux
/dev/sda11           3551        3824     2200873+  82  Linux swap / Solaris

Partition table entries are not in disk order

///////////////////////////////////////////////////////////////////////////////////////////////
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
# kopt=root=UUID=ae743a43-1e9a-4659-b10f-210fe22f974b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,9)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ae743a43-1e9a-4659-b10f-210fe22f974b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ae743a43-1e9a-4659-b10f-210fe22f974b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,9)
kernel		/boot/memtest86+.bin
quiet

title 		Windows XP 
rootnoverify 	(hd0,9)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by xtrm_redbull on 2007-12-12
Try [Super Grub]("http://supergrub.forjamari.linex.org/") I used it to boot my windows partition. But now I dont use windows anymore. :) Hope it helps

---

### Post by edm1 on 2007-12-12
> **Julius1988 said:**
> title 		Windows XP 
rootnoverify 	(hd0,**9**)
makeactive
chainloader +1

Your problem is this 9 in /boot/grub/menu.lst. It suggest XP is installed on /dev/sda10 which is clearly untrue since that is linux. Not quite sure where you have XP (sda5/6/7/8/9?) but you must change the 9 accordingly.

---

### Post by Julius1988 on 2007-12-12
in sda5

---

### Post by edm1 on 2007-12-12
Hopefully just change the 9 to 4.

---

### Post by edm1 on 2007-12-12
maybe back up first

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

---

### Post by Julius1988 on 2007-12-12
ill try & let u know in 5 mins

---

### Post by shafi on 2007-12-12
first open your terminal and type:
[html]
sudo gedit  /boot/grub/menu.lst
[/html]
then first delet the :

title Windows XP
rootnoverify (hd0,9)
makeactive
chainloader +1

that are exist at the end of your menue.lst

and then scroll up and find :    
#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1

then remove the # signs as follow
[html]
 title Windows 95/98/NT/2000
 root (hd0,0)
 makeactive
 chainloader +1
[/html]
save the file and reboot, then you will have windows xp into your grub list

---

### Post by Julius1988 on 2007-12-12
Invalid drive requested....press any key to continue....

---

### Post by subs on 2007-12-12
> **Julius1988 said:**
> Invalid drive requested....press any key to continue....

try to locate which partition ur windows is installed in... and change it to that..

just goto */media* and search around for ur windows partition

---

### Post by Julius1988 on 2007-12-12
here are three different versions.....but they have no effect at all
it still remains the same
-----------------------------------
title		Windows 95/98/NT/2000
 root		(hd0,0)
 makeactive
 chainloader	+1
---------------------------------------
title		Windows 95/98/NT/2000
 root		(hd0,4)
 makeactive
 chainloader	+1
---------------------------------------
title		Windows 95/98/NT/2000
 root		(hd0,5)
 makeactive
 chainloader	+1
-------------------------------------
windows installed in sda5

---

### Post by gaelfx on 2007-12-12
Julius what command did you run in that first post in order to print out all that information? Sorry, I'm not very good at all that command-line stuff, and I've recently repartitioned my drive so I could throw some XP on there for use with some Chinese programs, and I need to figure out how to more easily switch between the two. Also, could you tell me if starting up Windows from Grub will make it so that Grub is no longer on the MBR? I can't seem to get into Windows without breaking my Ubuntu boot loader. Thanks!

---

### Post by edm1 on 2007-12-12
```
sudo fdisk -l
```

---

### Post by gaelfx on 2007-12-12
Thanks edm.

---

### Post by Julius1988 on 2007-12-12
is there a way to resole this problem or should i re install everything for the sake of installing ubuntu:confused:

---

### Post by gaelfx on 2007-12-12
well, my WinXP is installed on sda2 and I added this to my grub menu.lst:

```

title                 Windows XP
root                (hd0,1)
makeactive
chainloader    +1
```

And I booted into windows without a hitch. It even kept grub in the MBR, much to my elation. Perhaps you have made a minor typographical error?

---

### Post by Julius1988 on 2007-12-12
first i installed xp & then i installed Ubuntu then booom my xp is gone............

---

### Post by Julius1988 on 2007-12-12
sda1 contains Ubuntu

---

### Post by Julius1988 on 2007-12-12
This is even more dreadful i cant burn any cd using Ubuntu to fix my mbr i am stranded out.....Is there any way out of this i can only hope...

---

### Post by gaelfx on 2007-12-12
ok, one more and then I will leave this alone, since I am not contributing much really.
Have you tried using VMware? If there is something that you really want to save, you may be able to do it with that. the instructions are here:
[http://ubuntuforums.org/showthread.php?t=631671]("http://ubuntuforums.org/showthread.php?t=631671")
Good luck!

---

### Post by bg_izrod on 2007-12-12
I hope you have a backup file of you grub.lst. Look at this lines (red) in the grub.lst:
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
[COLOR="Red"]default 0[/COLOR]

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR="Red"]timeout 3[/COLOR]

Try to change the timeout sequence to be at least 10 seconds. just type instead of 3 type 10 like follows:
[COLOR="Red"]timeout 10[/COLOR]

Then look if there is windows at all,  I guess windows is where it should be.

---

### Post by Julius1988 on 2007-12-13
at last i had no other go except to format everything!!!!!!!!!!:( anyway thanks for ur help guys...

---

