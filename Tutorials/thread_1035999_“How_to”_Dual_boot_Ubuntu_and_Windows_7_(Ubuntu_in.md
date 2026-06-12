---
title: "“How to” Dual boot Ubuntu and Windows 7 (Ubuntu installed first)"
date: 2009-01-10
forum: Tutorials
---

### Post by hyperdude111 on 2009-01-10
This thread is now obsolete. It will no longer work for current releases of Ubuntu. Please google around for newer guides. This thread is not being updated, it is not being checked, questions will not be answered and help will not be given. Please Let it die.

> &#8220;How to&#8221; Dual boot Ubuntu and Windows 7 (Ubuntu installed first)

##This guide does not work for Karamic or future releases, For that see page 14 and follow the link provided by presence1960 for how to dual boot with Grub2 (requires some reading) I will update this guide for grub2 when I have more time## 

I have recently seen many posts from people trying to dual boot Ubuntu and Windows 7 beta, but not succeeding. So I tried it out myself and found a solution.
Index
1.	Obtain a copy of Windows7.
2.	Partition your disk with gparted.
3.	Install Windows7.
4.	Re-install Grub.
5.	Edit Grub to List Windows 7.
6.	Have Fun.
__________________________________________________________________________________

1.	Obtain a copy of windows 7.  

*You can also find a torrent of this but for legal reasons I cannot provide a link. *


2.	Partition your disk 

**This does go wrong in some cases, if in doubt back up your valuable data.**

Boot from a Ubuntu live cd or a gparted live cd.
Start up gparted, If ubuntu is on the whole disk you need to re-size it by at least 8 gb for Windows 7. (Make sure windows 7 is on the second partition to make it easier for grub) You will be left with some unallocated space on your hard disk if you want you can partition it to NTFS or you can do it later on the windows install.

3.	Install Windows 7

Follow the on screen instructions, Select the un-partitioned space to format and install windows on, or if you already made it NTFS choose your NTFS partition. 

**It will ask for a product key but you have 30 days to do that. Note: Beta keys will work with the RC**

  
4.	Re-install GRUB

Now you have windows 7 but it has completely eaten your boot loader so you need to re-install grub. 
Boot from the ubuntu live cd and go to terminal.
Type in terminal:

"sudo grub"
"grub> find /boot/grub/stage1"

That should return your Ubuntu partition in the form of (hdX,Y), use that:

grub> root (hdX,Y)
grub> setup (hd0)
grub> quit

(you don&#8217;t need to type the grub> bit)

That has re-installed grub but you can no longer see windows7

5.	Edit grub.
Go to terminal from normal ubuntu and type :

&#8220;sudo gedit /boot/grub/menu.lst&#8221;

A large text file will open and at the bottom leave a line and add this:

title		windows 7 beta (Loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

(Do not type this line but if that does not work on re-boot try &#8220;hdo,0 or hd0,2&#8221; and so on until it works.)

 Now that is done you can re-boot  into windows 7 and ubuntu happily :)

******************Edit***********************
Hi
I have remembered that if you also have vista installed on your machine when you in install 7, that windows 7 will add itself to the vista bootloader.

So You will need to point grub to the vista partition so it will load the vista loader and give you the option for 7 and vista. 

Also To work out what partition number your 7 partiton is use gparted it will give you results like "Windows 7 sda2" that means hda0,2 or if you have two internal hard drives than change the tab in  the top right to the appropriate disk. Then take note of the sda2 but as it is on the 2nd drive it will be hda1,2. And so on.......... 
****************Edit*************************

---

### Post by meistercobbman on 2009-01-19
Thanks for the simple tutorial. I installed win7 on virtualbox and it took about 13GB though, not 8GB.

---

### Post by BLTicklemonster on 2009-01-21
Thank you! I installed Windows 7 on a spare hard drive with everything else unplugged so I could just turn the machine off and plug cables back in to run Ubuntu, not knowing if or how I could dual boot, so I'm glad to find this. I'll be trying this out tonight or tomorrow sometime and will come back whining when I hit a glitch, you know, lol.

I do have to say, W7 seems like they got it right. So far the best windows experience I've had with the one exception of using XP to download the first Ubuntu Live CD .iso file, that is. :)

So, I shouldn't have any problems if I just turn off, plug everything back in the way it was in the beginning, right?

---

### Post by csddavies on 2009-01-21
Excellent article.  Worked flawlessly.

---

### Post by damis648 on 2009-01-21
Nice little guide, but this pretty much applies to [any Windows installation when it is installed after Ubuntu]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

---

### Post by BLTicklemonster on 2009-01-22
Jeez, you'd think there was a way to determine which hd was which. I have 4, so it ought to be hd0 through hd3, but I can't get grub to work with one I know is in there no matter what entry I use. I know it's either hd1,1 or hd3,1 because hd0,1 and hd2,1 have ubuntu loaded on both of them, and the other hard drive is storage only. The one in question has two partitions, the first, hd*,0 would not be the operating system, but hd*1, the second partition is the one with the operating system. I edit menu.lst so reflect either hd1,1 or hd3,1, yet each time I try to select the drive at the grub menu, it says that's not a partition. Dang.

And I don't really want to go having to installing anything on a disk to use it...

Oh well.

By the way, the hard drive in question has windows loaded on it, and it was loaded with the drive in the machine by itself.

---

### Post by DSL5 on 2009-01-23
I tried this, but I now when I try to boot into Windows 7, I get the following:

BOOTMGR missing
Press Ctrl+Alt+Del to restart

What's going on??

I have XP in (hd0,0), Ubuntu in (hd0,4), and 7 in (hd0,2)

---

### Post by hyperdude111 on 2009-01-24
The Alt-Ctrl-Delete Problem normally happens to me after i have re-sized the windows partition after install to fix re install 7 and follow the rest of the guide. If this fails there may be a problem with your grub setup.

---

### Post by lftolen on 2009-01-24
I received the 
BOOTMGR missing
Press Ctrl+Alt+Del to restart
when I had selected the wrong partition to boot Windows 7.  Are you sure you are selecting the correct partition number?

---

### Post by marmel on 2009-01-25
Hi hyperdude111,

Thanks for the guide! Unfortunately it didn't work for me... :( When I boot Windows 7 via grub the system resets after trying to load Windows and no error message is displayed. I am sure that the partition number in the grub entry is correct (sda1 -> hd0,0).

Any suggestion?

Thank you so much!

---

### Post by yogo on 2009-01-26
I added Windows 7. So far I am impressed.
 
I have not reinstalled grub. Can I use BCDedit, the Vista bootloader program to add Ubuntu?

---

### Post by BLTicklemonster on 2009-01-26
Pfft, gone. I'd rather spend my time in Ubuntu anyway.

---

### Post by ceverhar on 2009-01-27
For those of you who are having problems with your BootMGR, read this: [http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221) If you still have problems with the MBR post there, it *should* still be active. I had a lot of problems with this, but that was because I installed Windows first.

---

### Post by hyperdude111 on 2009-01-27
Hi
I have remembered that if you also have vista installed on your machine when you in install 7, that windows 7 will add itself to the vista boot-loader.

So You will need to point grub to the vista partition so it will load the vista loader and give you the option for 7 and vista. 

Also To work out what partition number your 7 partiton is use gparted it will give you results like "Windows 7 sda2" that means hda0,2 or if you have two internal hard drives than change the tab in  the top right to the appropriate disk. Then take note of the sda2 but as it is on the 2nd drive it will be hda1,2. And so on..........

---

### Post by kinap on 2009-01-28
for the noobs like me, that have a hard time getting this to work.

be aware of the windows boot partition is NOT the installed partition (where you directed windows to while installing)

windows makes a second partition (it did in my case)

so i installed windows 7 on disk 3 partition 1.
and it made a 200MB partition on my disk 0 part 3.

so in menu.lst i had to point to that partition, after that it worked.

Kinap

---

### Post by Lovok on 2009-01-28
I've tried to install Win7 twice now, but my partition never shows up.
disk 1 : WinXP
disk 2 : Ubuntu 
  partition 1 : root (sda1)
  partition 2 : extended (sda3)
  partition 3 : unallocated (sda4)
  partition 4 : swap (sda2)

When I get to the part where I select the partition to install to, nothing from disk 2 shows up. I have also formatted the unallocated to NTFS (using fdisk, it doesn't let me in gparted) with no luck.

---

### Post by hyperdude111 on 2009-01-28
From what i can see you need to use gparted in ubuntu and look for the ntfs partition that is not ubuntu and that is 7

---

### Post by Athlon1 on 2009-01-28
Thanks for the guide.

Can you set up dual boot Ubuntu and Windows 7 if Windows 7 is installed first?

---

### Post by hyperdude111 on 2009-01-29
If windows 7 is installed first there are some problems. A new security feature means that if w7 is on the whole hdd you can not re-size the partition. If you had some magic luck and you installed w7 on an already dual partitioned space then it should work and follow this guide to add w7 to the grub menu.

---

### Post by Wickd on 2009-02-08
Well I get a Grub error 13 everytime I try and launch Windows 7 from my grub menu. Very weird

How do I get around this for instance?

Thanks

---

### Post by leenyx64 on 2009-02-11
thanks a lot for this post. i have just one problem.  when i try to boot the windows partion from grub. the screen just says "Starting up..." and hangs there. i have tried to reinstall and still it hangs. Has anyone had this problem. i am a noob and a little lost.

---

### Post by easybake on 2009-02-11
> **leenyx64 said:**
> thanks a lot for this post. i have just one problem.  when i try to boot the windows partion from grub. the screen just says "Starting up..." and hangs there. i have tried to reinstall and still it hangs. Has anyone had this problem. i am a noob and a little lost.

You are probably going to have to reinstall windows. If it gets to the "Windows is Starting" screen grub worked correctly.

---

### Post by dmber on 2009-02-21
I'd like to get this working.  Can I post my menu.lst and the output of something else and have you guys tell me what I'm doing wrong?

Thanks.

---

### Post by easybake on 2009-02-21
> **dmber said:**
> I'd like to get this working.  Can I post my menu.lst and the output of something else and have you guys tell me what I'm doing wrong?

Thanks.

Post the your /boot/grub/menu.lst and the output of ```
sudo fdisk -l
```

---

### Post by dmber on 2009-02-21
> **easybake said:**
> Post the your /boot/grub/menu.lst and the output of ```
sudo fdisk -l
```

menu.lst

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
# kopt=root=UUID=1250986f-e033-47c8-b5ae-fbb9cabe0dd2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1250986f-e033-47c8-b5ae-fbb9cabe0dd2

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		1250986f-e033-47c8-b5ae-fbb9cabe0dd2
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1250986f-e033-47c8-b5ae-fbb9cabe0dd2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		1250986f-e033-47c8-b5ae-fbb9cabe0dd2
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1250986f-e033-47c8-b5ae-fbb9cabe0dd2 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		1250986f-e033-47c8-b5ae-fbb9cabe0dd2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1250986f-e033-47c8-b5ae-fbb9cabe0dd2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		1250986f-e033-47c8-b5ae-fbb9cabe0dd2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1250986f-e033-47c8-b5ae-fbb9cabe0dd2 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		1250986f-e033-47c8-b5ae-fbb9cabe0dd2
kernel		/boot/memtest86+.bin
quiet

title		windows 7 beta (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

fdisk -l

```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f1990

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10241406   83  Linux
/dev/sda2            1276        1301      204800    7  HPFS/NTFS
/dev/sda3   *        1301        6992    45715456    7  HPFS/NTFS
/dev/sda4            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

```

Thanks.

---

### Post by easybake on 2009-02-21
> **dmber said:**
> 

Thanks.

Everything looks right. What exactly are you having issues with?

---

### Post by dmber on 2009-02-21
> **easybake said:**
> Everything looks right. What exactly are you having issues with?
when I try to get into Windows 7, it gives me a BOOTMGR error.

---

### Post by easybake on 2009-02-21
You are going to have to reinsert the windows 7 install disc and choose the repair option.

If this wipes out your grub you can reinstall it from a live disc.

---

### Post by dmber on 2009-02-21
> **easybake said:**
> You are going to have to reinsert the windows 7 install disc and choose the repair option.

If this wipes out your grub you can reinstall it from a live disc.
It seems like that's taking me in a circle.  I got to this point because installing Windows 7 wiped my grub.  Then I re-installed grub and now I get this BOOTMGR thing.  

I'll give it a shot, just letting you know my whole story.  Thanks.

---

### Post by rayman121985 on 2009-02-24
Anyone have any ideas on how to dual boot if you have Windows 7 installed first already? I have 2 hard drives...one has Windows 7 on it and the other is blank for Ubuntu...if it can be done...fingers crossed...anyone have a guide/tutorial for this?

THANKS!

::rayman:::guitar:

---

### Post by dmber on 2009-03-02
> **dmber said:**
> It seems like that's taking me in a circle.  I got to this point because installing Windows 7 wiped my grub.  Then I re-installed grub and now I get this BOOTMGR thing.  

I'll give it a shot, just letting you know my whole story.  Thanks.
Ok, I "repaired" Windows 7 -- which did say that I "had a problem with my startup" but I still get the same "missing bootmgr" message in GRUB.

Any new ideas?

---

### Post by dmber on 2009-03-02
i'm trying to figure out what the problem is.  Windows 7 made two partitions (both of which I can mount in Ubuntu).  One is 200 mb and houses a file called "bootmgr".  The other is 40some gigs and is my actual install of Windows 7.  When I open GParted in Ubuntu to see if my Windows 7 partition for Grub is HD0,1/2/3/etc., this is what it looks like:

[IMG]http://img408.imageshack.us/img408/263/gparted.png[/IMG]

Originally the "boot" flag was on the 40+ gig partition, but I keep getting errors, so I moved it to the 200gig partition (that has the bootmgr file).  Tried booting again, didn't work.  When I booted into Ubuntu, the boot flag had been moved back to the 40gig partition, though.  

Can someone help me with this, please?  As of right now, I can't get back into Windows 7.  Not a huge deal as I like Ubuntu better, but I can't sync up my iPhone or Nike+ Sportband without Windows 7.

Thanks.

---

### Post by dmber on 2009-03-16
Ok, got it working.  Now, how do I make Windows 7 the default boot option?

Here's my menu.lst:

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
# kopt=root=UUID=1250986f-e033-47c8-b5ae-fbb9cabe0dd2 ro

## default grub root device
## e.g. groot=(hd0,2)
# groot=1250986f-e033-47c8-b5ae-fbb9cabe0dd2

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		1250986f-e033-47c8-b5ae-fbb9cabe0dd2
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1250986f-e033-47c8-b5ae-fbb9cabe0dd2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		1250986f-e033-47c8-b5ae-fbb9cabe0dd2
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1250986f-e033-47c8-b5ae-fbb9cabe0dd2 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		1250986f-e033-47c8-b5ae-fbb9cabe0dd2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1250986f-e033-47c8-b5ae-fbb9cabe0dd2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		1250986f-e033-47c8-b5ae-fbb9cabe0dd2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1250986f-e033-47c8-b5ae-fbb9cabe0dd2 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		1250986f-e033-47c8-b5ae-fbb9cabe0dd2
kernel		/boot/memtest86+.bin
quiet

title		windows 7 beta (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Thanks.

---

### Post by easybake on 2009-03-16
> **dmber said:**
> Ok, got it working.  Now, how do I make Windows 7 the default boot option?

Here's my menu.lst:

Thanks.

change this ```
default		0

```
to 6 or the # of the listing you want to be the default boot.

---

### Post by Randy3011 on 2009-03-17
Hey all:
Just tried this and for the most part worked. Win7 has two partitions it creates during install.  The boot mgr is in (HD0,0). Once I pointed to that, everything works. Still want to have Ubuntu be the default.  Big Thanks to hyperdude111 for taking the time to work this out.

Randy3011

---

### Post by natsukashi on 2009-03-18
I have a problem, everything worked flawlessly until I tried to boot windows. The computer just kind of restarts itself. I've checked and Windows haven't made a separate partition, and I've also checked that I'm using the appropriate partition in my menu.lst

I'll give you my menu.lst and the result of fdisk -l and hopefully you'll be able to help me. :)

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
timeout		10

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
# kopt=root=UUID=5f9c3de4-5742-4eff-98c9-a1d9e84c2652 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5f9c3de4-5742-4eff-98c9-a1d9e84c2652

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		5f9c3de4-5742-4eff-98c9-a1d9e84c2652
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5f9c3de4-5742-4eff-98c9-a1d9e84c2652 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		5f9c3de4-5742-4eff-98c9-a1d9e84c2652
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5f9c3de4-5742-4eff-98c9-a1d9e84c2652 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		5f9c3de4-5742-4eff-98c9-a1d9e84c2652
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5f9c3de4-5742-4eff-98c9-a1d9e84c2652 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		5f9c3de4-5742-4eff-98c9-a1d9e84c2652
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5f9c3de4-5742-4eff-98c9-a1d9e84c2652 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		5f9c3de4-5742-4eff-98c9-a1d9e84c2652
kernel		/boot/memtest86+.bin
quiet
### END DEBIAN AUTOMAGIC KERNELS LIST

title windows 7 beta (Loader)
root (hd0,2)
savedefault
chainloader +1
makeactive
```

fdisk -l
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6c083d8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5099    40957686   83  Linux
/dev/sda2   *        5100        9567    35889210    7  HPFS/NTFS
/dev/sda3            9568       29646   161284567+   7  HPFS/NTFS
/dev/sda4           29647       30401     6064537+   5  Extended
/dev/sda5           29647       30401     6064506   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1bef3585

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sdb5               2       30401   244187968+   7  HPFS/NTFS

```

sda2 is my Windows partition. (It seems that something, probably Windows 7) has removed all my labels on the NTSF-drives.

---

### Post by easybake on 2009-03-18
> **natsukashi said:**
> I have a problem, everything worked flawlessly until I tried to boot windows. The computer just kind of restarts itself. 

sda2 is my Windows partition. (It seems that something, probably Windows 7) has removed all my labels on the NTSF-drives.
```

root (hd0,2)

```
In your menu.lst should be 
```

root (hd0,1)

```

---

### Post by natsukashi on 2009-03-19
I tried it and it didn't work. :/

I'm going to try to restore Windows and reinstall grub. Otherwise I'll just have to format the drive and reinstall Windows.

---

### Post by silvinator on 2009-04-27
Hi all,

Excuse my newbness but here's my question: I already have Vista dual booted with Ubuntu 8.10 but I would like to install Windows 7 over the Vista partition (i.e. I don't want Vista anymore as I cannot stand it) while keeping Intrepid in tact. Is there a way to do this? I've tried googling and browsing this forum for some clues but I can't seem to find anything that might help me with this. I thought maybe I could use the ubuntu "gparted" thing, which I've never used before, to just delete the contents of the vista partition? I would think that's possible because I can delete the ubuntu partition from the windows hard drive manager. Presumably, then, Windows 7 would install itself in the empty partition? Or am I just talking nonsense? Any help would be greatly appreciated :)

Cheers,
Silvie

---

### Post by wadeweldon on 2009-05-07
I would highly recommend booting to the live CD, when resizing a partition as this allows you to access the internet where you can return to this article as I have done.  I was also able to watch "Family Guy" and listen to Pandora radio. Thank you for the information.
Peace
Wade

---

### Post by easybake on 2009-05-07
> **silvinator said:**
> Hi all,

Excuse my newbness but here's my question: I already have Vista dual booted with Ubuntu 8.10 but I would like to install Windows 7 over the Vista partition (i.e. I don't want Vista anymore as I cannot stand it) while keeping Intrepid in tact. Is there a way to do this? I've tried googling and browsing this forum for some clues but I can't seem to find anything that might help me with this. I thought maybe I could use the ubuntu "gparted" thing, which I've never used before, to just delete the contents of the vista partition? I would think that's possible because I can delete the ubuntu partition from the windows hard drive manager. Presumably, then, Windows 7 would install itself in the empty partition? Or am I just talking nonsense? Any help would be greatly appreciated :)

Cheers,
Silvie

You can simply upgrade to windows 7 from your vista partition. Just boot into vista and put in the dvd. Click upgrade.

---

### Post by khristian on 2009-05-07
A friend of mine has this same problem, but it seems to have a little twist: he had WinXP and Ubuntu in dual-boot, without problems. After he installed Win7 over WinXP (formatted WinXP partition, performed clean install), grub was overwritten, as expected. But, when he attempted to restore grub using these commands, he ended up with a grub that booted ok into ubuntu, but listed "WinXP" as the windows entry, but unable to boot into Win7.
I've used these steps before many times, as they worked on my machine which has Ubuntu, WinXP, WinVista AND Win7 coexisting peacefully :P

His partition layout is:
hd0,0:win7
hd0,1:swap
hd0,2:ubuntu
hd0,3:/home

Any clues as to why this isn't working? thanks!

---

### Post by Heatherzilla on 2009-05-08
I currently have the Windows 7 beta and Ubuntu dual booted on my laptop (windows installed first) but now that the RC has been released I want to install that instead of the beta. How would I go about doing this? Do I just delete the beta and install the RC in the free space? And am I likely to have to play around with GRUB to get everything working properly?

---

### Post by javafool on 2009-05-08
Great post! Worked like a charm. I had been trying EasyBCD but apparently the Windows 7 boot loader is ever so slightly different than Vista's.  Now, if I could get my Syntek webcam to work in 9.04 - but that's another thread. Thanks again!

---

### Post by hyperdude111 on 2009-05-09
> **Heatherzilla said:**
> I currently have the Windows 7 beta and Ubuntu dual booted on my laptop (windows installed first) but now that the RC has been released I want to install that instead of the beta. How would I go about doing this? Do I just delete the beta and install the RC in the free space? And am I likely to have to play around with GRUB to get everything working properly?

Just format the beta partition and install the RC.

Then do the steps in the guide to restore the grub bootloader from live cd.

Then follow the steps to re-name from beta to RC.

Then it should work.

---

### Post by hyperdude111 on 2009-05-09
> **khristian said:**
> A friend of mine has this same problem, but it seems to have a little twist: he had WinXP and Ubuntu in dual-boot, without problems. After he installed Win7 over WinXP (formatted WinXP partition, performed clean install), grub was overwritten, as expected. But, when he attempted to restore grub using these commands, he ended up with a grub that booted ok into ubuntu, but listed "WinXP" as the windows entry, but unable to boot into Win7.
I've used these steps before many times, as they worked on my machine which has Ubuntu, WinXP, WinVista AND Win7 coexisting peacefully :P

His partition layout is:
hd0,0:win7
hd0,1:swap
hd0,2:ubuntu
hd0,3:/home

Any clues as to why this isn't working? thanks!

It may be to do with that windows 7 takes over the winxp bootloader.

---

### Post by Prozzy on 2009-05-10
> **hyperdude111 said:**
> 
[QUOTE=khristian;7232061]A friend of mine has this same problem, but it seems to have a little twist: he had WinXP and Ubuntu in dual-boot, without problems. After he installed Win7 over WinXP (formatted WinXP partition, performed clean install), grub was overwritten, as expected. But, when he attempted to restore grub using these commands, he ended up with a grub that booted ok into ubuntu, but listed "WinXP" as the windows entry, but unable to boot into Win7.
I've used these steps before many times, as they worked on my machine which has Ubuntu, WinXP, WinVista AND Win7 coexisting peacefully :P

His partition layout is:
hd0,0:win7
hd0,1:swap
hd0,2:ubuntu
hd0,3:/home

Any clues as to why this isn't working? thanks!

It may be to do with that windows 7 takes over the winxp bootloader.[/QUOTE]

Yeah i had WinXP and Ubuntu in dual boot, then installed Win7 on another partition on the same drive. The Win7 bootloader is now used to boot Win7 and WinXP - to get WinXP i have to choose "earlier versions" in the Win7 bootloader.

But great howto, worked like a charm!

---

### Post by Lateralus138 on 2009-05-10
This is exactly the thing I was looking for when I googled my inquiry. I have two seperate hard drives that are not on the same line (no master/slave). Windows Vista is on the 1st hard drive and Ubuntu is on the 2nd ard drive and I want to dual boot Windows 7 with the Ubuntu drive. I will let you know how it turns out.

---

### Post by Lateralus138 on 2009-05-11
HI, like I said before I am installing Windows 7 2nd to Ubuntu on a 2nd hard drive. When I installed Ubuntu I installed grub to the disk with Ubtuntu and not Vista so that Instead of having gurb load automatically, Vista will load automatically and if I want the grub loader to load then I have to hold f10 to go into the boot menu and boot the 2nd disk. I want it to be the same when I reinstall Grub so what are the commands for that? The 1st drive with Vista is SDA and the 2nd drive with Ubuntu that I will be installing 7 is SDB

---

### Post by Lateralus138 on 2009-05-11
Ok, nevermind I guess. I installed Windows 7 to my second hard drive with Ubuntu and my Grub loader is still installed on the second drive while I can access Windows 7 from the loader. So 7 and Vista are my first two options and if I want to load Ubuntu then I just go to the boot menu (F10) and boot the second drive.

---

### Post by khristian on 2009-05-11
> **hyperdude111 said:**
> It may be to do with that windows 7 takes over the winxp bootloader.

Well, it was expected: upon installing 7 it would overwrite the XP bootloader, including a reference to it in an "Earlier version of Windows" entry. The problem was that, when performing the steps to restore grub, it would result in the vista/7 loader being corrupted.
After some more trials, the problem was solved by reinstalling Ubuntu... go figure.
Anyway, I've adopted a different approach now: I've installed Ubuntu, 7, installed the Ubuntu bootloader to its root partition, and used EasyBCD to add an entry referencing that bootloader to the Vista/7 bootloader.
No more bootloader updates for me, as long as I don't reinstall windows.

---

### Post by Cain67 on 2009-05-24
ok, i have a problem
was running windows 7 on the 4th part of partition.
then installed ubuntu on the first partition.

i have followed your awesome guide, but no matter which i load, (hdd0,0,1,2,3) it wont work...

i have a 500gb hdd.
first is 12gb partition, with ubuntu installed.
2nd and 3rd are 200gb partitions with files on.
4th is the windows 7 partition.

someone please help!
cheers

---

### Post by hyperdude111 on 2009-05-24
> **Cain67 said:**
> ok, i have a problem
was running windows 7 on the 4th part of partition.
then installed ubuntu on the first partition.

i have followed your awesome guide, but no matter which i load, (hdd0,0,1,2,3) it wont work...

i have a 500gb hdd.
first is 12gb partition, with ubuntu installed.
2nd and 3rd are 200gb partitions with files on.
4th is the windows 7 partition.

someone please help!
cheers


I think your problem is that you are typing hdd0,2 hdd0,3  in grub istead of hda0,1 hda 0,2 .

I think that hda0,4 or hda0,5 or hda0,6 will boot win7 from your setup

---

### Post by Cain67 on 2009-05-24
ok, slight hitch, you were right about the hdd issue and so i have corrected that.
however iv listed the options for partitions, and it recognizes the 4 partitions.

0=ubuntu
4,5 = data
6=windows 7

however, when setting the first line to (hd0,6) it come up with
invalid device requested

any ideas???
cheers

---

### Post by Cain67 on 2009-05-25
ok, new issue:
missing NTLDR press ctrl+alt+del to restart

was given a link to a NTLDR iso which worked... until i selected the correct partition and screen went black.

---

### Post by hyperdude111 on 2009-05-25
> **Cain67 said:**
> ok, new issue:
missing NTLDR press ctrl+alt+del to restart

was given a link to a NTLDR iso which worked... until i selected the correct partition and screen went black.

AH You can now boot into win7 BUT your windows install is corrupted. This happened to me when i re-sized the win partition after install. 

Your only choice is to re-install windows 7 the do what you did earlier. (On a positive note you already know what partition it is, so it should be a lot easier)

Good Luck

---

### Post by Ubuntme70 on 2009-05-26
Well, was not from ubuntu first but was second just had to flip flop hard drives cause the drive with 7 on it did not have a boot manager file :oops: used windows 7 install disk to write the Bmgr on the 7 drive!!
Works fine now!

---

### Post by fathafiga on 2009-05-28
Hello, and thanks so much for this walk-through. I followed it, and sadly my machine reboots and goes right back into GRUB every time I select "windows 7 beta (Loader)" from the boot menu. I'm 100% sure I have the correct partition selected in menu.lst (hda0,1). (When I select the incorrect partition, it gives me the "Cannot find Boot Manager" error.)

I followed this guide to a T with the exception of two minor(?) details:

1) I did not use GParted to create the partitions. I used the Ubuntu installer to create them during an old install. I created one for Ubuntu and one for Windows 7, and installed each OS respectively. Then I re-installed both OSes over both partitions so that I could follow this guide. I didn't think it would matter how the partitions got created.

2) I'm using the newer release candidate of Windows 7 rather than the original beta. I figured the process would be the same for each version of Windows 7. Maybe I was wrong?

I don't think this particular reboot issue has been resolved directly in this thread. I'm not sure where to go from here. Should I use GParted to wipe this entire drive clean of partitions and create new ones? Or perhaps the Windows 7 RC1 has some booting issues that the older beta didn't have. Sorry to resurrect this ancient thread, but any advice would be much appreciated.

---

### Post by hyperdude111 on 2009-05-29
> **fathafiga said:**
> Hello, and thanks so much for this walk-through. I followed it, and sadly my machine reboots and goes right back into GRUB every time I select "windows 7 beta (Loader)" from the boot menu. I'm 100% sure I have the correct partition selected in menu.lst (hda0,1). (When I select the incorrect partition, it gives me the "Cannot find Boot Manager" error.)

I followed this guide to a T with the exception of two minor(?) details:

1) I did not use GParted to create the partitions. I used the Ubuntu installer to create them during an old install. I created one for Ubuntu and one for Windows 7, and installed each OS respectively. Then I re-installed both OSes over both partitions so that I could follow this guide. I didn't think it would matter how the partitions got created.

2) I'm using the newer release candidate of Windows 7 rather than the original beta. I figured the process would be the same for each version of Windows 7. Maybe I was wrong?

I don't think this particular reboot issue has been resolved directly in this thread. I'm not sure where to go from here. Should I use GParted to wipe this entire drive clean of partitions and create new ones? Or perhaps the Windows 7 RC1 has some booting issues that the older beta didn't have. Sorry to resurrect this ancient thread, but any advice would be much appreciated.


1. I doubt using the RC will make any differences, it is still the same OS with a few bug fixes and it has not affected anything with me.

2. The way you set up the partitions is fine, a partition is always the same the tool you use to do it doesn't matter.
-------------------------------------------------------------------------
On to your problem, i would **guess** the partition you have labled in your menu.lst is wrong. Just to be sure make about 4 different entries in your grub with hda0,0 then hda0,1 then hda0,2 and try that. If win7 is on partition one it will be hda0,0 not 1.

If that does not work try a full re-format the follow the guide from the beginning but only do this if there is nothing important on that hard drive because you will lose EVERYTHING. But the most likely problem is your grub setup so play with that. 

BTW You can change the name from beta to RC or whatever you want, i just never bothered updating this thread. I should also post a link to the RC but i CBA. 

Good Luck

---

### Post by adifire on 2009-06-07
I've a situation. Initially I'd 3 OS, ubuntu, vista and win 7. Then my vista crashed and I thought I'd format it. But then later I realised that the Windows7 boot depends on vista's. So without vista, 7 won't boot (shows bootmgr missing) and now I've ubuntu. 
I tried figuring out how wimdows 7 boots, but there's no bootmgr file, nor boot.ini or any boot file for that matter I've noticed when only win7 is installed (I seperately installed it on virtual box).

Is there any way I can reload Win7 without having to reinstall it? :confused: I know it's ubuntu forums, but hey if you guys know, let me know to!!!

---

### Post by easybake on 2009-06-07
You should be able to restore the windows boot loader from a windows 7 install disc. Its the "repair" option. If that works you will probably have to reinstall grub from a live cd.

---

### Post by hyperdude111 on 2009-06-07
> **easybake said:**
> You should be able to restore the windows boot loader from a windows 7 install disc. Its the "repair" option. If that works you will probably have to reinstall grub from a live cd.

That should work, but you will have to re-install grub following the steps from the guide after.

---

### Post by Ac1ds0ld13r on 2009-06-07
Ok, I know I'm probably back tracking here a bit, but if the directions to do this are in here I cannot make sense of them.
 
2 Harddrives. hd0,1 has Ubuntu on it. 
 
The brand new hd0,5? (I'm assuming 5 because BIOS is saying its device 5) is where I want Win7 to go. 
 
When I try to install windows to it I get:
 
Setup was unable to create a new system partition or locate an existing system partition. See Setup log files for more information. (I can't find a way to get to those log files). 
 
Now, I'm assuming "system partition" is referring to the same "System" Disk 0 Partition 1 on hd0,1. But isn't that where Ubuntu is installed? and if I install win7 there won't it overwrite ubuntu? also noticed the system partition is 288GB versus the logical partition (partition 2) is 10gb. 
 
I figured worse comes to worse I start with windows and work my way down (since that seems to be the preferred way to do this anyway) and tried to install windows on the system partition, but i cannot format it.
 
What am i doing wrong? 
 
I'd love some help with this. My Yahoo ID is Ac1ds0ld13r and I'm signed in if its easier to communicate that way. I can also dl an IRC client if necessary. 
 
I've gone through tutorial after tutorial and I'm about to take the thing outside and run it over with my car. :(


EDIT: Found out when I disconnected hd0,1 from the motherboard Windows read the second drive and installed correctly without a problem. Not sure why I needed to do that, but meh. If anyone else has this issue thats the solution I found.

---

### Post by easybake on 2009-06-08
> **Ac1ds0ld13r said:**
> Ok, I know I'm probably back tracking here a bit, but if the directions to do this are in here I cannot make sense of them.
 
2 Harddrives. hd0,1 has Ubuntu on it. 
 
The brand new hd0,5? (I'm assuming 5 because BIOS is saying its device 5) is where I want Win7 to go.  Do you mean new hard drive or partition. hd0,5. Means disk 1 partition number 6. This is the same disk that has your Ubuntu on it. 


> When I try to install windows to it I get:
 
Setup was unable to create a new system partition or locate an existing system partition. See Setup log files for more information. (I can't find a way to get to those log files). 
 
Now, I'm assuming "system partition" is referring to the same "System" Disk 0 Partition 1 on hd0,1. But isn't that where Ubuntu is installed? and if I install win7 there won't it overwrite ubuntu? also noticed the system partition is 288GB versus the logical partition (partition 2) is 10gb. 
This problem may becaused because you can't create another primary partition. I believe the number of primary partitions is limited to 3 possibly 4. And if your system is already up to hd0,6. You may have used up all of your primary partition slots.
 
> I figured worse comes to worse I start with windows and work my way down (since that seems to be the preferred way to do this anyway) and tried to install windows on the system partition, but i cannot format it.
It may not let you edit partitions that are currently in use. Be sure to unmount any partitions before you try to format them.

> EDIT: Found out when I disconnected hd0,1 from the motherboard Windows read the second drive and installed correctly without a problem. Not sure why I needed to do that, but meh. If anyone else has this issue thats the solution I found.
I guess I should have read this first.

---

### Post by S3NATOR on 2009-06-11
OK, I've got this working with 2 hard drives. I've got Ubuntu 9.04 on hd(0,0) and Win7 on hd(1,0). But I keep running into one problem. If I boot into Win7 and then restart my PC I can't get back into grub. I have to reinstall grub with a Live CD every time I reboot from Win7. It works fine when I reboot from Ubuntu. I've done some searching in the forums and still can't find a fix. I'm sure it's something simple in grub that needs to be changed. Please help.

Thanks,
S3N

---

### Post by easybake on 2009-06-11
> **S3NATOR said:**
> OK, I've got this working with 2 hard drives. I've got Ubuntu 9.04 on hd(0,0) and Win7 on hd(1,0). But I keep running into one problem. If I boot into Win7 and then restart my PC I can't get back into grub. I have to reinstall grub with a Live CD every time I reboot from Win7. It works fine when I reboot from Ubuntu. I've done some searching in the forums and still can't find a fix. I'm sure it's something simple in grub that needs to be changed. Please help.

Thanks,
S3N

Which hdd do you have as your main boot disk in the bios?

---

### Post by S3NATOR on 2009-06-12
> **easybake said:**
> Which hdd do you have as your main boot disk in the bios?

Sorry for the delayed response. This is my work computer so I had to wait till I got to work to check the bios. It looks like it's booting from the Ubuntu hard drive but it's kinda hard to tell. I haven't seen a bios setup like this PC. In the boot order menu it has a "Hard Drive" option but it doesn't allow you to choose which hard drive. It just says "SATA Integrated".

After I reboot from Win7 grub says this:
> Grub Loading stage 1.5
It just hangs there and won't boot any further. The keyboard is also locked up at this point.

---

### Post by easybake on 2009-06-12
> **S3NATOR said:**
> Sorry for the delayed response. This is my work computer so I had to wait till I got to work to check the bios. It looks like it's booting from the Ubuntu hard drive but it's kinda hard to tell. I haven't seen a bios setup like this PC. In the boot order menu it has a "Hard Drive" option but it doesn't allow you to choose which hard drive. It just says "SATA Integrated".If that is the case, there is usually a second menu somewhere in the bios where you can set the hard disk priority. Try and check every menu in your bios, it could be buried somewhere. I'm guessing this is where the problem lies.

---

### Post by S3NATOR on 2009-06-17
> **easybake said:**
> If that is the case, there is usually a second menu somewhere in the bios where you can set the hard disk priority. Try and check every menu in your bios, it could be buried somewhere. I'm guessing this is where the problem lies.
Well I've been trying on and off for a few days now to find a way to set hard disk priorities in my bios but can't even find the option on [HP's manual](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c00814591).

But now that's the least of my problems LOL! I screwed something up and now I can't get back into Win7. I think I tried to setup grub on the wrong HD once and now when I try to boot into Win7 grub says "Grub Loading Stage2" and then reverts right back to the grub menu and doesn't boot into Win7. Luckily I can still get into Ubuntu and everything. Did I overwrite windows bootloader or something when I ran grub setup on (hd1,0) which is my Win7 partition? I can't even mount the Win7 hard drive any more LOL!

Edit: Well I was able to do a repair on my Win7 partition and I can get back into Windows. But I still lose grub after I log into Win7 and reboot. I still haven't found a way to change my SATA priorities.

---

### Post by strangepork on 2009-06-23
Ive been round and round with this, making progress i think.  

Now I am to the stage where I THINK it should work, but the win7 gives me

starting up...

and never does anything

Win7 repair says its working fine! 

Heres the quick version of what i did:

sda 1 - swap
sda 2 - /

sdb - second drive with /usr partition


1) used gparted to make 100G room on sda.
2) win7 wont install until i remove 'special' partition from sda1 aka swap
3) win7 installs great on sda 3 (numbers off a bit but you get idea)
4) as expected, grub hosed.  try to boot off of 9.04 livecd
5) livecd wont boot with massive readfs errors until i finally get a prompt and makeswap and swapon sda1 again
6) livecd is fine now, reinstall grub
7) win7 now broken, repair says its fine tho. install ms-sys and fix mbr for /sda
8) boot to ubuntu, edit grub list to point to 0,0 for win (after trying a ton of combinations), and get

Starting up...

then nothing.  again, win 7 disk says no need to repair it, should be working =/

any ideas?

strangepork@slortar:~$ sudo fdisk -l
[sudo] password for strangepork: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ee646

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             487       30401   240292237+   5  Extended
/dev/sda5             487       15784   122881153+  83  Linux
/dev/sda6           15785       30401   117409792    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c219f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux
strangepork@slortar:~$ 

GRUB

strangepork@slortar:~$ cat /boot/grub/menu.lst
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        8

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=b8b58b6f-0a65-4b68-a09c-4619f458483b ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=b8b58b6f-0a65-4b68-a09c-4619f458483b

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        b8b58b6f-0a65-4b68-a09c-4619f458483b
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=b8b58b6f-0a65-4b68-a09c-4619f458483b ro xforcevesa quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        b8b58b6f-0a65-4b68-a09c-4619f458483b
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=b8b58b6f-0a65-4b68-a09c-4619f458483b ro xforcevesa  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        b8b58b6f-0a65-4b68-a09c-4619f458483b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b8b58b6f-0a65-4b68-a09c-4619f458483b ro xforcevesa quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        b8b58b6f-0a65-4b68-a09c-4619f458483b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b8b58b6f-0a65-4b68-a09c-4619f458483b ro xforcevesa  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        b8b58b6f-0a65-4b68-a09c-4619f458483b
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows 7 Ultimate 1
root (hd0,0)
savedefault
makeactive
chainloader +1


Thanks in advance!!

---

### Post by hyperdude111 on 2009-06-24
I would try a re-install of win7. If that fails re-download and try again.

---

### Post by TSWMIN85 on 2009-07-02
Thanks worked flawlessly.

):P

---

### Post by spree89 on 2009-07-04
I have been trying to do this for hours. It's 3AM and I don't know what to do. I've been messing around with the menu.ist, at first i've been getting the "Starting up ..." screen that dosen't go anywhere, so I tried this guy's thread [http://ubuntuforums.org/showthread.php?t=1037421](http://ubuntuforums.org/showthread.php?t=1037421)
when I booted up Windows 7 grub restarts, so I continued trying to get this dual boot to work, sometimes I get this "Error 18" message, other times grub continues to restart, and once I got the "Starting up ... " screen again. I'm a total noob and I really need help.

Here's my menu.lst:
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=962739a2-0743-4799-86b0-7adb9a159310 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=962739a2-0743-4799-86b0-7adb9a159310

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        962739a2-0743-4799-86b0-7adb9a159310
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=962739a2-0743-4799-86b0-7adb9a159310 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        962739a2-0743-4799-86b0-7adb9a159310
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=962739a2-0743-4799-86b0-7adb9a159310 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        962739a2-0743-4799-86b0-7adb9a159310
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=962739a2-0743-4799-86b0-7adb9a159310 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        962739a2-0743-4799-86b0-7adb9a159310
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=962739a2-0743-4799-86b0-7adb9a159310 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        962739a2-0743-4799-86b0-7adb9a159310
kernel        /boot/memtest86+.bin
quiet

title windows 7 beta (Loader)
root (hd0,1)
chainloader +1
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)

### END DEBIAN AUTOMAGIC KERNELS LIST
```and here's my partitions

---

### Post by easybake on 2009-07-04
> **spree89 said:**
> I have been trying to do this for hours. It's 3AM and I don't know what to do. I've been messing around with the menu.ist, at first i've been getting the "Starting up ..." screen that dosen't go anywhere, so I tried this guy's thread [http://ubuntuforums.org/showthread.php?t=1037421](http://ubuntuforums.org/showthread.php?t=1037421)
when I booted up Windows 7 grub restarts, so I continued trying to get this dual boot to work, sometimes I get this "Error 18" message, other times grub continues to restart, and once I got the "Starting up ... " screen again. I'm a total noob and I really need help.

Here's my menu.lst:
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=962739a2-0743-4799-86b0-7adb9a159310 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=962739a2-0743-4799-86b0-7adb9a159310

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        962739a2-0743-4799-86b0-7adb9a159310
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=962739a2-0743-4799-86b0-7adb9a159310 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        962739a2-0743-4799-86b0-7adb9a159310
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=962739a2-0743-4799-86b0-7adb9a159310 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        962739a2-0743-4799-86b0-7adb9a159310
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=962739a2-0743-4799-86b0-7adb9a159310 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        962739a2-0743-4799-86b0-7adb9a159310
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=962739a2-0743-4799-86b0-7adb9a159310 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        962739a2-0743-4799-86b0-7adb9a159310
kernel        /boot/memtest86+.bin
quiet

title windows 7 beta (Loader)
root (hd0,1)
chainloader +1
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)

### END DEBIAN AUTOMAGIC KERNELS LIST
```and here's my partitions

Have you tried reinstalling windows 7. It seems as there is barely enough space allocated for it. Only 9gigs is pushing the limit for windows 7.

---

### Post by mailbuntu on 2009-07-04
thanks so much for this excellent guide! am able to get windows 7 listed on the grub menu. however when i choose it, my computer kinda restarts itself then i get to the grub menu again.

no problems with booting into ubuntu 9.04

would anyone be able to help me out? thx :)

---

### Post by hyperdude111 on 2009-07-06
> **mailbuntu said:**
> thanks so much for this excellent guide! am able to get windows 7 listed on the grub menu. however when i choose it, my computer kinda restarts itself then i get to the grub menu again.

no problems with booting into ubuntu 9.04

would anyone be able to help me out? thx :)

You have a non-existent partition listed as windows 7. 

In the place of hd0,0 try hd0,1 or hd0,2 or hd0,3 or hd0,4 or hd0,5 and so on.

When you find one that works stick with it.

---

### Post by thonuz on 2009-07-08
When installing Windows 7 don't let it create the 200mB partitions is all you really need. See here. [http://www.mydigitallife.info/2009/01/09/how-to-avoid-200mb-hidden-system-partition-from-been-created-during-windows-7-installation/](http://www.mydigitallife.info/2009/01/09/how-to-avoid-200mb-hidden-system-partition-from-been-created-during-windows-7-installation/)

When windows tries to recover from an error it may use some of the recovery files here. After that ubuntu had problems loading. With grub 2 expect problems.

For the other way around
1. Partition your drive using partition magic: say in my case 40% for ntfs, 5 Gb Swap, the rest Ext 4
2. Install Windows 7 and make sure to click cancel when prompted for the 200m partition. See link above. 
3. Install Ubuntu

---

### Post by heroidi on 2009-07-09
I just translated it into albanian think you like it:
[http://ayih.org/tips_tricks/si_te_beni_dual_boot_ubuntu_me_windows_7_ubuntu_te_jete_i_pari_i_instaluar-t5554.0.html;msg21398#new](http://ayih.org/tips_tricks/si_te_beni_dual_boot_ubuntu_me_windows_7_ubuntu_te_jete_i_pari_i_instaluar-t5554.0.html;msg21398#new)

---

### Post by Barquero on 2009-07-13
Worked a treat, many thanks.  Before I read this I was prepared to replace XP w/ 7 and then re-install Ubuntu, the labour saving is appreciated.

---

### Post by SpecialKxm107 on 2009-07-14
Hi all,

I've been following the guide (up until setting up grub to load the Windows 7 RC partition) and I'm getting the dreaded BOOTMGR not found press CTRL ALT DELETE to restart error. I'm almost 100% positive that I have the correct partition for Win7 RC (hd0,2) but it will not let me boot the OS. I've tried numbers 0 through 4 as well and it gives me the other error saying that the partition wasn't found.

Here is the end of my menu.lst (only text I've added/changed in the file):

title Windows 7 RC (loader)
root (hd0,2)
savedefault
makeactive
chainloader +1

When I load up gparted this is what I have for my partitions:

/dev/sda1  ext3  73.24gb - ubuntu
/dev/sda2  ntfs   100mb
/dev/sda3  ntfs   216.10gb - W7 RC (this one has the boot flag set)
/dev/sda4  extended  8.65gb
     /dev/sda5 linux-swap  8.65gb

I've tried repairing my Windows install with the RC dvd but that did absolutely nothing: still can't find the BOOTMGR and if I don't press ESC to get into the Grub Menu, my pc just loads Ubuntu by default. I've tried this guide from scratch twice with 2 reinstalls of W7 (I really don't want to remove my Ubuntu Partition).

This is driving me nuts, any ideas and help would be greatly appreciated. Thanks.

---

### Post by hyperdude111 on 2009-07-14
> **SpecialKxm107 said:**
> Hi all,

I've been following the guide (up until setting up grub to load the Windows 7 RC partition) and I'm getting the dreaded BOOTMGR not found press CTRL ALT DELETE to restart error. I'm almost 100% positive that I have the correct partition for Win7 RC (hd0,2) but it will not let me boot the OS. I've tried numbers 0 through 4 as well and it gives me the other error saying that the partition wasn't found.

Here is the end of my menu.lst (only text I've added/changed in the file):

title Windows 7 RC (loader)
root (hd0,2)
savedefault
makeactive
chainloader +1

When I load up gparted this is what I have for my partitions:

/dev/sda1  ext3  73.24gb - ubuntu
/dev/sda2  ntfs   100mb
/dev/sda3  ntfs   216.10gb - W7 RC (this one has the boot flag set)
/dev/sda4  extended  8.65gb
     /dev/sda5 linux-swap  8.65gb

I've tried repairing my Windows install with the RC dvd but that did absolutely nothing: still can't find the BOOTMGR and if I don't press ESC to get into the Grub Menu, my pc just loads Ubuntu by default. I've tried this guide from scratch twice with 2 reinstalls of W7 (I really don't want to remove my Ubuntu Partition).

This is driving me nuts, any ideas and help would be greatly appreciated. Thanks.

That problem you have is a problem, It means you have selected the correct partition but it cant boot, do you have xp or vista instlalled?

I would recommend a re-install, I know its boring but its all i can thunk of.

---

### Post by SpecialKxm107 on 2009-07-14
I don't have XP or Vista installed. Should I remove Windows7 and try and get Vista to work in a dual boot on the remaining free space on my hd? I'd assume if I can get the Vista Bootloader to work then Windows 7 would be located under that loader (as you stated in the guide). Or could I just upgrade Vista to W7 when I know I can boot it? I really don't need to have a copy of Vista as I won't use it. Thanks for the help.

---

### Post by hyperdude111 on 2009-07-14
> **SpecialKxm107 said:**
> I don't have XP or Vista installed. Should I remove Windows7 and try and get Vista to work in a dual boot on the remaining free space on my hd? I'd assume if I can get the Vista Bootloader to work then Windows 7 would be located under that loader (as you stated in the guide). Or could I just upgrade Vista to W7 when I know I can boot it? I really don't need to have a copy of Vista as I won't use it. Thanks for the help.

I would just format your 7 partition and re-install then follow the guide from there.

---

### Post by zarthon on 2009-07-19
> **damis648 said:**
> Nice little guide, but this pretty much applies to [any Windows installation when it is installed after Ubuntu]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

NOTE: This procedure also covers a specific problem with Windows7 installer Partition editor. ( avoid using it) 
But your link is a great help to those having GRUB issues !

---

### Post by Batstroke on 2009-08-02
So funnily enough I need instructions on how to dual boot Ubuntu with Widows 7 first. Is there I forum anywhere I can find for that?

---

### Post by watson.william.w on 2009-08-04
If you don't have any particular attachment to your files/settings/anything you can't back up you can always load up Ubuntu with a Live CD and wipe all partitions off the drive. I just finished installing W7 and Ubuntu (8.10) on a new drive, so I didn't need to save anything. To do this you:

1. Boot up a Live CD and open GParted. Wipe all old partitions on the drive and create 2 new partitions. Mine were ~60GB/~55GB. To save some effort make partition 2 NTFS (I left partition 1 as ext2). Shut down Ubuntu and take out the Live CD when it prompts you, replacing it with the Windows disc.

2. Let the windows installer run, and when you are prompted, select partition 2 to install into. Complete the W7 installation.

Edit ----> partition 2 may be labeled as 'partition 1', and partition 1 may be labeled as 'partition 0'.

3. When everything is done reboot back into the Ubuntu Live CD and select the 'Install' option. Configure date/time/location/language etc. When you get to the partitioning page, select the first 'Guided' option to install on partition 1. Guided option 2 will wipe windows off the drive. Finish the Ubuntu install.

4. GRUB should automatically see the W7/longhorn partition and allow you to boot into that.


So basically, if you aren't installing W7 after you install Ubuntu you don't need to reinstall or repair Grub. Install W7 first on partition 2, then Ubuntu on partition 1 and it should all come out peachy.

W

---

### Post by Hashimi on 2009-08-07
I installed ubuntu with wubi. I can see the grub from my windows 7. How can i reinstall and edit grub now?

Thanks for help.

---

### Post by Hashimi on 2009-08-07
Anyone help?

---

### Post by xbunti on 2009-08-07
I followed the steps above and had severe problems - not sure why.

I had ubuntu 9 already installed in my pc with one 750gb HD
which had about 7 partitions with ubunto OS installed in
the first 100GB partition which was primary.

I shrunk the ubuntu primary partition from 100gb to 50gb and
the set the 50gb freed up as NTFS.

Then I put in windows 7 dvd and rebooted and went past first 3 screens
and in the screen to choose the partition to install windows I chose
the new 50gb ntfs partition i had created above and clicked next button.

The windows 7 install kept spinning for over 2 hours and
the only way I could get out of it was to use reset button in my pc.

I removed windows dvd and rebooted and found ubuntu works fine and
all my ubuntu files seem to be there.

However, my HD partion table seems to be completely messed up !!

Before the windows7 install attempt my fdisk used to show :

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000bf9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6086    48885763+  83  Linux
/dev/sda2   *        6087       11185    40957717+   7  HPFS/NTFS
/dev/sda3           11186       91201   642728520    5  Extended
/dev/sda5           11186       12181     8000338+  82  Linux swap / Solaris
/dev/sda6           12182       30413   146448508+  83  Linux
/dev/sda7           30414       78453   385881268+  83  Linux
/dev/sda8           12182       30413   146448508+  83  Linux

and now it shows :

Warning: omitting partitions after #60.
They will be deleted if you save this partition table.

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000bf9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6086    48885763+  83  Linux
/dev/sda2   *        6087       11185    40957717+   7  HPFS/NTFS
/dev/sda3           11186       91201   642728520    5  Extended
/dev/sda5           11186       12181     8000338+  82  Linux swap / Solaris
/dev/sda6           12182       30413   146448508+  83  Linux
/dev/sda7           30414       78453   385881268+  83  Linux
/dev/sda8           12182       30413   146448508+  83  Linux
/dev/sda9           30414       78453   385881268+  83  Linux
/dev/sda10          12182       30413   146448508+  83  Linux
/dev/sda11          30414       78453   385881268+  83  Linux
/dev/sda12          12182       30413   146448508+  83  Linux
/dev/sda13          30414       78453   385881268+  83  Linux
/dev/sda14          12182       30413   146448508+  83  Linux
/dev/sda15          30414       78453   385881268+  83  Linux
/dev/sda16          12182       30413   146448508+  83  Linux
/dev/sda17          30414       78453   385881268+  83  Linux
/dev/sda18          12182       30413   146448508+  83  Linux
/dev/sda19          30414       78453   385881268+  83  Linux
/dev/sda20          12182       30413   146448508+  83  Linux
...............................
................................
...............................
/dev/sda59          30414       78453   385881268+  83  Linux
/dev/sda60          12182       30413   146448508+  83  Linux

and gparted shows /dev/sda with just one partition for who disk
and in its drop down list of drives it shows the list
/dev/sda then /dev/sda100, sda101, sda102...... etc... to /dev/sda255
and no entries between /dev/sda1 to /dev/sda99

How can I fix this messed up partion info ??
Please help !!

If this portends what windows 7 is to be then it seems pretty grim
not to mention it failed to install.

---

### Post by hyperdude111 on 2009-08-08
> **Hashimi said:**
> I installed ubuntu with wubi. I can see the grub from my windows 7. How can i reinstall and edit grub now?

Thanks for help.

Windows 7 and wubi are not yet compatible.

---

### Post by pimchu on 2009-08-09
thanks mate, will need it someday.:)

---

### Post by ngrieb on 2009-08-14
Did this with 2 HDD's but when I load grub Windows 7 seems to think that I screwed up its MBR and wants to recover \BOOT\MBR, but if I do it eats grub. I keep playing tug of war. sdb1 = (hd1,0) correct? Any suggestions? I have old HDD's and Ubuntu is the primary master, Win 7 is primary slave and DVD drive is secondary master. Has anyone had similar problems and a solution? Thanks.

---

### Post by zach-okeefe on 2009-08-14
I have tried every possible combination of suggestions given in this thread, with little luck.  I am able to get into Ubuntu fine, but no combination I use, either editing GRUB itself (trying different setup (hdX,Y) as I have seen people use hd0, but also some have said to use the same destination that you set as your root, which is the one returned by the find /boot/grub/stage1 command) or editing my menu.lst (tried combinations from hd0,1 up to hd0,9 , even though i know i don't have that many partitions. 

I'll post my fdisk and menu.lst, but don't think i'm an idiot if they are completely retarded looking right now, as I've gotten more and more desperate trying to find the right combination.  Hopefully someone can see my problem right away?
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19175   154023156    7  HPFS/NTFS
/dev/sda2   *       19176       25230    48636787+   b  W95 FAT32
/dev/sda3           25231       30401    41536057+   5  Extended
/dev/sda5           25231       30183    39784941   83  Linux
/dev/sda6           30184       30401     1751053+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60800   488375968+   b  W95 FAT32
```


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
# kopt=root=UUID=1fb5fe99-944a-4171-9dba-b5eeb42cb76f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1fb5fe99-944a-4171-9dba-b5eeb42cb76f

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

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		1fb5fe99-944a-4171-9dba-b5eeb42cb76f
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=1fb5fe99-944a-4171-9dba-b5eeb42cb76f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		1fb5fe99-944a-4171-9dba-b5eeb42cb76f
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=1fb5fe99-944a-4171-9dba-b5eeb42cb76f ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		1fb5fe99-944a-4171-9dba-b5eeb42cb76f
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=1fb5fe99-944a-4171-9dba-b5eeb42cb76f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		1fb5fe99-944a-4171-9dba-b5eeb42cb76f
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=1fb5fe99-944a-4171-9dba-b5eeb42cb76f ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		1fb5fe99-944a-4171-9dba-b5eeb42cb76f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=1fb5fe99-944a-4171-9dba-b5eeb42cb76f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		1fb5fe99-944a-4171-9dba-b5eeb42cb76f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=1fb5fe99-944a-4171-9dba-b5eeb42cb76f ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
uuid		1fb5fe99-944a-4171-9dba-b5eeb42cb76f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1fb5fe99-944a-4171-9dba-b5eeb42cb76f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid		1fb5fe99-944a-4171-9dba-b5eeb42cb76f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1fb5fe99-944a-4171-9dba-b5eeb42cb76f ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, memtest86+
uuid		1fb5fe99-944a-4171-9dba-b5eeb42cb76f
kernel		/boot/memtest86+.bin
quiet

title Windows 7 RC (Loader)
root (hd0,2)
savedefault
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Please give suggestions here, or feel free to email me with help.  Thanks in advance!

---

### Post by Synt_x on 2009-08-14
Try root hd(1,0) for Windows R7 (Disk 2, partition 1)

---

### Post by Promille on 2009-08-14
Thanks for a great guide :) I began to worry when i saw no grub after installing win7, but it was as i thought fortunately. 

Just a little heads up, probably said before, but i dont wanna read through ten pages; 

Even though win7 writes over vista, if you install on same partition, nothing is changed in the menu.lst file, so grub still thinks vista is on that partition, when infact win7 is. Therefore, when you run the Vista (Loader) from grub, you actually run win7. This can easily be fixed by just changing the name from Vista (loader) or whatever to Windows 7 (Loader) or what you find appropiate in the /boot/grub/menu.lst file. Just something I encountered during this process. 

-Promille

---

### Post by hyperdude111 on 2009-08-14
> **zach-okeefe said:**
> I have tried every possible combination of suggestions given in this thread, with little luck.  I am able to get into Ubuntu fine, but no combination I use, either editing GRUB itself (trying different setup (hdX,Y) as I have seen people use hd0, but also some have said to use the same destination that you set as your root, which is the one returned by the find /boot/grub/stage1 command) or editing my menu.lst (tried combinations from hd0,1 up to hd0,9 , even though i know i don't have that many partitions. 

I'll post my fdisk and menu.lst, but don't think i'm an idiot if they are completely retarded looking right now, as I've gotten more and more desperate trying to find the right combination.  Hopefully someone can see my problem right away?
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19175   154023156    7  HPFS/NTFS
/dev/sda2   *       19176       25230    48636787+   b  W95 FAT32
/dev/sda3           25231       30401    41536057+   5  Extended
/dev/sda5           25231       30183    39784941   83  Linux
/dev/sda6           30184       30401     1751053+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60800   488375968+   b  W95 FAT32
```


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
# kopt=root=UUID=1fb5fe99-944a-4171-9dba-b5eeb42cb76f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1fb5fe99-944a-4171-9dba-b5eeb42cb76f

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

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		1fb5fe99-944a-4171-9dba-b5eeb42cb76f
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=1fb5fe99-944a-4171-9dba-b5eeb42cb76f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		1fb5fe99-944a-4171-9dba-b5eeb42cb76f
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=1fb5fe99-944a-4171-9dba-b5eeb42cb76f ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		1fb5fe99-944a-4171-9dba-b5eeb42cb76f
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=1fb5fe99-944a-4171-9dba-b5eeb42cb76f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		1fb5fe99-944a-4171-9dba-b5eeb42cb76f
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=1fb5fe99-944a-4171-9dba-b5eeb42cb76f ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		1fb5fe99-944a-4171-9dba-b5eeb42cb76f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=1fb5fe99-944a-4171-9dba-b5eeb42cb76f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		1fb5fe99-944a-4171-9dba-b5eeb42cb76f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=1fb5fe99-944a-4171-9dba-b5eeb42cb76f ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
uuid		1fb5fe99-944a-4171-9dba-b5eeb42cb76f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1fb5fe99-944a-4171-9dba-b5eeb42cb76f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid		1fb5fe99-944a-4171-9dba-b5eeb42cb76f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1fb5fe99-944a-4171-9dba-b5eeb42cb76f ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, memtest86+
uuid		1fb5fe99-944a-4171-9dba-b5eeb42cb76f
kernel		/boot/memtest86+.bin
quiet

title Windows 7 RC (Loader)
root (hd0,2)
savedefault
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Please give suggestions here, or feel free to email me with help.  Thanks in advance!

This will work for you.

title Windows 7 RC (Loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

You need partition (hd0,0) what fdisk reads as sda1 = hd0,0 in grub. I will soon make this more clear in the guide but whatever fdisk or gparted tells you for grub the number is -1 so:

sda1 = hd0,0
sda2 = hd0,1
sda3 = hd0,2

And so on....

---

### Post by zach-okeefe on 2009-08-17
Ah, that's probably the one combination I didn't think to try.  I forgot that the list most likely started at hd0,0 , but this seems really obvious now.  I'll let you know how it goes.

Edit:  That did it!  Thank you sooooooooooo much.

---

### Post by enaction on 2009-08-17
Thank you for that easy to do fix for my lost grub after a WinXP reinstall!  I really appreciate it!

---

### Post by fusionstrings on 2009-08-21
Last two days I spend following all the tips trics described in this thread. But I am unable to make my Windows 7 and Ubuntu 9 running as dual boot.

I'd Windows XP and ubuntu running successfully then I installed Windows 7 by deleting the XP partition and installing windows 7 there. It created 100 MB extra partition automatically and installed it self successfully. Then I followed this thread and re-installed grub. Now grub installed but even after using "sudo gedit /boot/grub/menu.lst" and adding windows 7 entry I am not able to run Windows 7. 

Then I learned 100 MB extra partition creates some problem, Then I used XP CD to delete Windows 7 partitions and created new partition and re installed Windows 7. But again same result. 

While changing the combination from "root (hd0,0)" to "root (hd0,9)" I am getting different behavior. 

"root (hd0,0)" restarts automatically and presents boot menu. While using different combination some times it shows "Error 13, no proper device found, Windows is starting and press any key to continue".  After pressing any key it returns me to boot menu. 

I am not sure where I am possibly wrong, Its great most of you managed to make it working so I am optimistic about mine. I don't want to re install ubuntu coz I don't want to loose packages installed.

Following is my fdisk and menu.lst. I am not convinced that not using gparted might have some impact. In case if you thing that is the reason.

[SIZE=3]_**Fdisk**_[/SIZE]
```

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x537f537f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30715542+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            3825        9733    47464042+   f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda5            3825        5129    10482381    7  HPFS/NTFS
/dev/sda6            5130        7041    15358108+   7  HPFS/NTFS
/dev/sda7            7042        7284     1951866   82  Linux swap / Solaris
/dev/sda8            7285        9733    19671561   83  Linux

```[SIZE=3]_**menu.lst**_[/SIZE]
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bb252b8e-969c-49e7-babd-b582ed949088

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-3-rt
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-3-rt root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-3-rt
quiet

title        Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode)
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-3-rt root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro  single
initrd        /boot/initrd.img-2.6.28-3-rt

title        Ubuntu 9.04, memtest86+
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title        Microsoft Windows XP Professional
#rootnoverify    (hd0,0)
#savedefault
#makeactive
#chainloader    +1

title Windows 7 RC-1 (Loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

```All helps are appreciated and thanks in advance. :)

---

### Post by hyperdude111 on 2009-08-21
> **fusionstrings said:**
> Last two days I spend following all the tips trics described in this thread. But I am unable to make my Windows 7 and Ubuntu 9 running as dual boot.

I'd Windows XP and ubuntu running successfully then I installed Windows 7 by deleting the XP partition and installing windows 7 there. It created 100 MB extra partition automatically and installed it self successfully. Then I followed this thread and re-installed grub. Now grub installed but even after using "sudo gedit /boot/grub/menu.lst" and adding windows 7 entry I am not able to run Windows 7. 

Then I learned 100 MB extra partition creates some problem, Then I used XP CD to delete Windows 7 partitions and created new partition and re installed Windows 7. But again same result. 

While changing the combination from "root (hd0,0)" to "root (hd0,9)" I am getting different behavior. 

"root (hd0,0)" restarts automatically and presents boot menu. While using different combination some times it shows "Error 13, no proper device found, Windows is starting and press any key to continue".  After pressing any key it returns me to boot menu. 

I am not sure where I am possibly wrong, Its great most of you managed to make it working so I am optimistic about mine. I don't want to re install ubuntu coz I don't want to loose packages installed.

Following is my fdisk and menu.lst. I am not convinced that not using gparted might have some impact. In case if you thing that is the reason.

[SIZE=3]_**Fdisk**_[/SIZE]
```

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x537f537f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30715542+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            3825        9733    47464042+   f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda5            3825        5129    10482381    7  HPFS/NTFS
/dev/sda6            5130        7041    15358108+   7  HPFS/NTFS
/dev/sda7            7042        7284     1951866   82  Linux swap / Solaris
/dev/sda8            7285        9733    19671561   83  Linux

```[SIZE=3]_**menu.lst**_[/SIZE]
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bb252b8e-969c-49e7-babd-b582ed949088

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-3-rt
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-3-rt root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-3-rt
quiet

title        Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode)
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-3-rt root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro  single
initrd        /boot/initrd.img-2.6.28-3-rt

title        Ubuntu 9.04, memtest86+
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title        Microsoft Windows XP Professional
#rootnoverify    (hd0,0)
#savedefault
#makeactive
#chainloader    +1

title Windows 7 RC-1 (Loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

```All helps are appreciated and thanks in advance. :)

Ok it looks like your windows install is corrupted, delete the win7 partition then re-install in the same space. After that follow the guide starting from "Restore grub"

You should use hd0,0 for your grub but if that wont work experiment with others. 

Don't delete any extra partition win7 creates, it has not caused me any problems or anyone else in this thread (it could even be the cause of your issue)

Good luck.

---

### Post by fusionstrings on 2009-08-21
Thanks for replying, Well I tried all possible combination (hd0,0) to (hd0,9) and again (hd1,0) to (hd1,9) in case. With all above described two installations. Now just I tried my third installation and this time I partitioned my HDD with gparted. I am using (hd0,0) but again I successfully got my ubuntu and lost win7. While choosing win7 its reverting me to boot menu again.

I am pasting my new fdisk and menu.lst

[SIZE=3]_**FDisk**_[/SIZE]
 ```

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x537f537f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        9733    47464042+   f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda5            3825        5129    10482381    7  HPFS/NTFS
/dev/sda6            5130        7041    15358108+   7  HPFS/NTFS
/dev/sda7            7042        7284     1951866   82  Linux swap / Solaris
/dev/sda8            7285        9733    19671561   83  Linu

```

[SIZE=3]_**Menu.lst**_[/SIZE]
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bb252b8e-969c-49e7-babd-b582ed949088

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-3-rt
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-3-rt root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-3-rt
quiet

title        Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode)
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/vmlinuz-2.6.28-3-rt root=UUID=bb252b8e-969c-49e7-babd-b582ed949088 ro  single
initrd        /boot/initrd.img-2.6.28-3-rt

title        Ubuntu 9.04, memtest86+
uuid        bb252b8e-969c-49e7-babd-b582ed949088
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title        Microsoft Windows XP Professional
#rootnoverify    (hd0,0)
#savedefault
#makeactive
#chainloader    +1

title Windows 7 RC-1 (Loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

```

---

### Post by hyperdude111 on 2009-08-21
What are all three NTFS partitions for ?

---

### Post by ripper9100 on 2009-08-22
Thank you for the guide, with your help I was able to successfully replace XP with the Professional Edition of Windows 7 with no problems.

---

### Post by fusionstrings on 2009-08-24
> **hyperdude111 said:**
> What are all three NTFS partitions for ?
These are for windows file storage of course, since windows can't see linux partitions and ubuntu can so I use ntfs for file storage and other dedicated partition for OS. anyway I am still on hung and decided to postpone using ubuntu since my efforts were not working and currently I am using win 7.

Ubuntu is still just one grub recovery away and I desperately want to use dual boot. but since windows is more important for me because of photoshop so I want to try only full proof solution. once again thanks for giving time and trying to help :). I just fallen in love to ubuntu and have installed a torrent of apps and I am quite become fond of it.

Its sad I can't use it. but anyway.

---

### Post by kamssada on 2009-08-25
Hey 
I have an issue, I mapped all the drives, and i am able to dual boot, the problem is that everytime i boot into windows 7, it erases my grub and i have to root and setup, into the grub with the live cd. 

Any one has clues of why that's happening to me?

---

### Post by hyperdude111 on 2009-08-26
> **kamssada said:**
> Hey 
I have an issue, I mapped all the drives, and i am able to dual boot, the problem is that everytime i boot into windows 7, it erases my grub and i have to root and setup, into the grub with the live cd. 

Any one has clues of why that's happening to me?

Windows 7 is trying to install the windows bootloader.

Can you please say which version of win7 you are using. (check desktop watermark)

Also what media are you booting from, separate hd or dvd etc.

A common fix I found for some issues was to just re-install and the second time it was fine.

---

### Post by Good at Sports on 2009-08-30
Hi, I have Ubuntu 9.04 and I added a partition to install Windows 7. Install worked fine and I installed a driver for my video card before restoring my grub. I added the following into my boot:

title w7
root (hd0,3)
makeactive
chainloader+1

when I boot, it says, "Error 12: Invalid Device, press any key to continue," or something close to that. I'm sure windows 7 is in hd(0,3) and I've tried all of my partitions and it won't boot. Any suggestions? Thanks in advance.

---

### Post by Gatekeeper_NZ on 2009-08-31
Thanks for the guide. Very helpful :)

---

### Post by crystaldart on 2009-08-31
Thank you very much for the tut friend. That was a real breather.

// but met a slight twist from above tut. mentioning it here in case some1 finds it helpful//

I use dual boot. Just installed Win 7. And there goes my Grub loading.
I followed your tutorial. And Got back the Grub.

But, from step 5

" root     (hd0,1) " did not work
   root        (hd1,1) ---------- did not work

and so on.

But in my Grub, it showed "Windows XP SP3" as one option and at the last
"Windows 7 bootloader" (Which never worked when choosen)

So I gave a try to "Windows XP SP3", Magically it logged me on to my Win 7 log on screen.

I hope using "sudo gedit /boot/grub/menu.ls"  I could change the Option Name. Will give it a try.

But thank you all for the help :)

---

### Post by hyperdude111 on 2009-08-31
> **crystaldart said:**
> Thank you very much for the tut friend. That was a real breather.

// but met a slight twist from above tut. mentioning it here in case some1 finds it helpful//

I use dual boot. Just installed Win 7. And there goes my Grub loading.
I followed your tutorial. And Got back the Grub.

But, from step 5

" root     (hd0,1) " did not work
   root        (hd1,1) ---------- did not work

and so on.

But in my Grub, it showed "Windows XP SP3" as one option and at the last
"Windows 7 bootloader" (Which never worked when choosen)

So I gave a try to "Windows XP SP3", Magically it logged me on to my Win 7 log on screen.

I hope using "sudo gedit /boot/grub/menu.ls"  I could change the Option Name. Will give it a try.

But thank you all for the help :)


You can change the name by editing the file. Its quite easy.

I assume you installed windows 7 over WXP SP3 then yes grub option for wxp will now take you to win7

---

### Post by ..::Ryan::.. on 2009-09-04
I have tried using hd0,1 - 5 and none of them will load 7. Any ideas from looking at the fdisk as to what I should use?

I tried hd1,0 and it said starting up... and sat there and did nothing.

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x108d0a57

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9563    76814766   83  Linux
/dev/sda2            9564       19457    79473555    f  W95 Ext'd (LBA)
/dev/sda5            9564       19457    79473523+   7  HPFS/NTFS

``````

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=b93dd274-291b-495a-a7bf-225d574876db ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b93dd274-291b-495a-a7bf-225d574876db

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        b93dd274-291b-495a-a7bf-225d574876db
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=b93dd274-291b-495a-a7bf-225d574876db ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        b93dd274-291b-495a-a7bf-225d574876db
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=b93dd274-291b-495a-a7bf-225d574876db ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        b93dd274-291b-495a-a7bf-225d574876db
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b93dd274-291b-495a-a7bf-225d574876db ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        b93dd274-291b-495a-a7bf-225d574876db
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b93dd274-291b-495a-a7bf-225d574876db ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        b93dd274-291b-495a-a7bf-225d574876db
kernel        /boot/memtest86+.bin
quiet

title        Windows 7 (Loader)
root        (hd0,1)
savedefault
makeactive
chainloader +1
### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by rickyprose on 2009-09-08
Excellent articole, easy and simple understandable for everyone!!!

Ciao

Ricky

---

### Post by l_o_s_b on 2009-09-19
Thank you for this nice guide. Works perfect here.

---

### Post by BUKRITYA on 2009-09-21
Great post, and the replies from everyone were helpful.

If any of you find trouble make sure you go through hd0-2 and partitions 0-3, that is in the menu.lst try:hd0,0 then hd0,1 hd0,2 hd0,3 , then try the same with hd1,0 etc. 
my gparted showed me that 7 was on hda1 which is supposed to be hd0,1 but it turned out on hd0,0
also I had the screen where I had to choose "start windows normally", and then it worked!
THANX, my friends have been having problems with this, MS is trying to confuse the enemy, those SOBs...

---

### Post by Joshka89 on 2009-09-28
I'm having some issues here.

So i did a fresh install of Ubuntu first with boot on /dev/sda1
the rest of linux is on /dev/sda5 under /dev/sda2

then i install windows 7 with a separate boot partition as well so it looks like this:

/dev/sda1 -linux boot
/dev/sda2 -ext
      /dev/sda5 -linux
/dev/sda3 -windows 7 boot
/dev/sda4 -windows 7

here is my fdisk -l output: 
```
joshka@joshka-laptop:~$ sudo -i
[sudo] password for joshka: 
root@joshka-laptop:~# fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82208220

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  83  Linux
/dev/sda2              13        6091    48829567+   5  Extended
/dev/sda3            6092        6104      102400    7  HPFS/NTFS
/dev/sda4   *        6104       14594    68190208    7  HPFS/NTFS
/dev/sda5              13        6091    48829536   83  Linux

```Her is my menu.lst:
```
## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        df87b61f-f118-47b5-8218-0c15ffe66a20
kernel        /vmlinuz-2.6.28-15-generic root=UUID=4243fd9a-5679-4757-bd84-b122ae922d95 ro quiet splash 
initrd        /initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        df87b61f-f118-47b5-8218-0c15ffe66a20
kernel        /vmlinuz-2.6.28-15-generic root=UUID=4243fd9a-5679-4757-bd84-b122ae922d95 ro  single
initrd        /initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        df87b61f-f118-47b5-8218-0c15ffe66a20
kernel        /vmlinuz-2.6.28-11-generic root=UUID=4243fd9a-5679-4757-bd84-b122ae922d95 ro quiet splash 
initrd        /initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        df87b61f-f118-47b5-8218-0c15ffe66a20
kernel        /vmlinuz-2.6.28-11-generic root=UUID=4243fd9a-5679-4757-bd84-b122ae922d95 ro  single
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        df87b61f-f118-47b5-8218-0c15ffe66a20
kernel        /memtest86+.bin
quiet

title        Windows 7
rootnoverify    (hd0,2)
makeactive
chanloader    +1
### END DEBIAN AUTOMAGIC KERNELS LIST
```Problem is, if i go to my boot list at GRUB startup and select Windows 7, the screen does nothing... just nothing at all.

If i pick (hd0,1) or (hd0,4) I get Error 12: Invalid device requested. Any other combinations do nothing at all

Help would be appreciated. Windows 7 was working prior to GRUB reinstall


EDIT=========================
Ok so I was going to boot Windows recovery from the CD but instead it booted WINDOWS itself, gave me an error and restarted the computer.
Windows boot has once again placed itself as the boot on my MBR. If i go to gparted the boot flag is on sda4. if i change it back to sda1 then Ubuntu loads fine.

This is getting annoying.

More EDIT=====================
So i got the W7 cd to get to repair console
it repaired windows...
which then replaced the boot flag to sda4 again
which then made GRUB not boot

so i used the Livecd to change the Boot flag to sda1 again
It appears that this whole operation is purely dependent upon the boot flag. More help please

---

### Post by presence1960 on 2009-09-28
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Joshka89 on 2009-09-28
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 94273 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda5 and 
                       looks at sector 95297 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on the same partition for 
                       /boot/grub/stage2.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x82208220

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       192,779       192,717  83 Linux
/dev/sda2             192,780    97,851,914    97,659,135   5 Extended
/dev/sda5             192,843    97,851,914    97,659,072  83 Linux
/dev/sda4          98,058,240   234,438,655   136,380,416   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="df87b61f-f118-47b5-8218-0c15ffe66a20" TYPE="ext2" 
/dev/sda4: UUID="5A5CCCDE5CCCB5D3" TYPE="ntfs" 
/dev/sda5: UUID="4243fd9a-5679-4757-bd84-b122ae922d95" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
/dev/sda1 on /boot type ext2 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/joshka/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=joshka)


============================= sda1/grub/menu.lst: =============================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=4243fd9a-5679-4757-bd84-b122ae922d95 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=df87b61f-f118-47b5-8218-0c15ffe66a20

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        df87b61f-f118-47b5-8218-0c15ffe66a20
kernel        /vmlinuz-2.6.28-15-generic root=UUID=4243fd9a-5679-4757-bd84-b122ae922d95 ro quiet splash 
initrd        /initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        df87b61f-f118-47b5-8218-0c15ffe66a20
kernel        /vmlinuz-2.6.28-15-generic root=UUID=4243fd9a-5679-4757-bd84-b122ae922d95 ro  single
initrd        /initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        df87b61f-f118-47b5-8218-0c15ffe66a20
kernel        /vmlinuz-2.6.28-11-generic root=UUID=4243fd9a-5679-4757-bd84-b122ae922d95 ro quiet splash 
initrd        /initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        df87b61f-f118-47b5-8218-0c15ffe66a20
kernel        /vmlinuz-2.6.28-11-generic root=UUID=4243fd9a-5679-4757-bd84-b122ae922d95 ro  single
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        df87b61f-f118-47b5-8218-0c15ffe66a20
kernel        /memtest86+.bin
quiet

title        Windows 7
rootnoverify    (hd0,4)
makeactive
chanloader    +1
### END DEBIAN AUTOMAGIC KERNELS LIST

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd.img-2.6.28-11-generic
    .0GB: initrd.img-2.6.28-15-generic
    .0GB: vmlinuz-2.6.28-11-generic
    .0GB: vmlinuz-2.6.28-15-generic

=========================== sda5/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=4243fd9a-5679-4757-bd84-b122ae922d95 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=df87b61f-f118-47b5-8218-0c15ffe66a20

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        df87b61f-f118-47b5-8218-0c15ffe66a20
kernel        /vmlinuz-2.6.28-15-generic root=UUID=4243fd9a-5679-4757-bd84-b122ae922d95 ro quiet splash 
initrd        /initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        df87b61f-f118-47b5-8218-0c15ffe66a20
kernel        /vmlinuz-2.6.28-15-generic root=UUID=4243fd9a-5679-4757-bd84-b122ae922d95 ro  single
initrd        /initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        df87b61f-f118-47b5-8218-0c15ffe66a20
kernel        /vmlinuz-2.6.28-11-generic root=UUID=4243fd9a-5679-4757-bd84-b122ae922d95 ro quiet splash 
initrd        /initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        df87b61f-f118-47b5-8218-0c15ffe66a20
kernel        /vmlinuz-2.6.28-11-generic root=UUID=4243fd9a-5679-4757-bd84-b122ae922d95 ro  single
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        df87b61f-f118-47b5-8218-0c15ffe66a20
kernel        /memtest86+.bin
quiet

title        Windows 7
rootnoverify    (hd0,4)
makeactive
chanloader    +1
### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=4243fd9a-5679-4757-bd84-b122ae922d95 /               ext3    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=df87b61f-f118-47b5-8218-0c15ffe66a20 /boot           ext2    relatime        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


    .1GB: boot/grub/menu.lst
    .1GB: boot/grub/stage2
    .1GB: boot/initrd.img-2.6.28-11-generic
    .1GB: boot/initrd.img-2.6.28-15-generic
    .1GB: boot/vmlinuz-2.6.28-11-generic
    .1GB: boot/vmlinuz-2.6.28-15-generic
    .1GB: initrd.img
    .1GB: initrd.img.old
    .1GB: vmlinuz
    .1GB: vmlinuz.old
```

Its 3 am right now so I'm gonna go to bed. Hope to continue this tomorrow.
I have a Windows 7 USB installer ready so if this gets too complicated i'll just switch around my install order

---

### Post by presence1960 on 2009-09-28
change this in menu.lst :
```
title        Windows 7
rootnoverify    (hd0,4)
makeactive
chanloader    +1
```

to

```
title           Windows 7
rootnoverify    (hd0,3)
chanloader      +1
```

---

### Post by ptolomy_was_right on 2009-10-08
Help! I was running Ubuntu and Vista Ultimate dual loading and instead of clean installing Win 7 Ultimate over Vista I did a straight upgrade. Lost the Ubuntu boot of course but used the live Cd to edit grub and get it back... but was horrified to discover the dual boot had gone back to Ubuntu/Vista, not Ubuntu/Win 7!! Ok finally figured out how to make Win 7 appear on boot with Ubuntu instead of Vista but it still half-tries to boot up Vista. It gets to Win 7 in the end, but something's not right - the new Win 7 loading screen doesn't appear, an old Vista one does, and then it flashes some weird test-pattern-like thing across the screen before Win 7 appears. And Win 7 doesn't always get there, either. Just crashes sometimes.
Help, anyone?!!

Okay, reupgraded Win 7 using the DVD, so that's all well and good, but back to square 1 with Ubuntu, ie no dual boot. Easiest way, anybody? (I realise I've got to run the Ubuntu live disc first and edit the grub, but I did something wrong last time becuase, yes I got Ubuntu back on the boot but Win 7 wasn't there, Vista was (I had upgraded to Win 7 from Vista). How can I do this safely?

---

### Post by presence1960 on 2009-10-08
> **ptolomy_was_right said:**
> Help! I was running Ubuntu and Vista Ultimate dual loading and instead of clean installing Win 7 Ultimate over Vista I did a straight upgrade. Lost the Ubuntu boot of course but used the live Cd to edit grub and get it back... but was horrified to discover the dual boot had gone back to Ubuntu/Vista, not Ubuntu/Win 7!! Ok finally figured out how to make Win 7 appear on boot with Ubuntu instead of Vista but it still half-tries to boot up Vista. It gets to Win 7 in the end, but something's not right - the new Win 7 loading screen doesn't appear, an old Vista one does, and then it flashes some weird test-pattern-like thing across the screen before Win 7 appears. And Win 7 doesn't always get there, either. Just crashes sometimes.
Help, anyone?!!
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by ptolomy_was_right on 2009-10-08
No need my friend, worked this time no problems. Cheers!! \\:D/

Hmmm... now what was that someone told me about Mac OS booting on PC... triple boot with Leopard... dare I??? Does it work (Leopard on VAIO with Core 2 Duo Intel chip and motherboard; and is the triple boot possible?!) :rolleyes:

---

### Post by carlson_song on 2009-10-09
Interestting, I will try!

---

### Post by easybake on 2009-10-12
> **ptolomy_was_right said:**
> No need my friend, worked this time no problems. Cheers!! \\:D/

Hmmm... now what was that someone told me about Mac OS booting on PC... triple boot with Leopard... dare I??? Does it work (Leopard on VAIO with Core 2 Duo Intel chip and motherboard; and is the triple boot possible?!) :rolleyes:

I've only ran into problems with it. It's much easier done from a Mac base. Then you would just boot camp and use Refit. Done and Done. 

But with mac's they use the Darwin bootloader which can be a huge pain in the ***. If you get any luck with it please let me know. I think I was trying it with a Kalyway OSX 86 disc. You might have better luck than I did.

I never got past "HFS+ parition error"

---

### Post by ptolomy_was_right on 2009-10-12
there's an online guide "How to Triple Boot MAC OS X, Windows 7 and Ubuntu..." in a forum: [http://forums.techarena.in/guides-tutorials/1135890.htm](http://forums.techarena.in/guides-tutorials/1135890.htm) 
I will be trying soon.. I'll let you know the results!

---

### Post by UbFreak on 2009-10-12
Thanks for this. And speaking of osx86, it took me a year to finally realize i burned the dvd wrong.:)

---

### Post by ptolomy_was_right on 2009-10-14
> **UbFreak said:**
> Thanks for this. And speaking of osx86, it took me a year to finally realize i burned the dvd wrong.:)
Think OSX86 more likely to work than Leopard?

---

### Post by Altay_H on 2009-10-16
I tried this exact procedure last week, and it didn't go as smoothly as I expected. My Ubuntu 9.04 install is on an ext4 partition, and for some bizarre reason the Windows 7 RC installer unallocated the ext4 partition even though it was not the partition Windows 7 RC was told to use. Windows 7 RC itself booted up without any problems, but Ubuntu 9.04 was completely lost (in theory).

After learning how to use TestDisk I was able to restore the ext4 partition, fix grub, and boot back into Ubuntu, but destroyed the Windows 7 RC install in the process. Is there any way to ensure Windows 7 RC won't unallocate ext4 partitions while installing? I suspect the easiest solution might be to convert the ext4 partition to ext3, install Windows 7 RC, then (optionally) convert it back to ext4.


UPDATE:
I recently tried installing Windows 7 RC on the same computer again. The only thing I did differently this time was I allocated an NTFS partition for Windows 7 RC using Gparted rather than leaving the partition for Windows 7 unallocated. Windows 7 RC installed exactly as it should, without touching the Ubuntu partition. I'm guessing Windows 7 RC might have trouble installing onto unallocated space and prefers NTFS-formatted partitions.

---

### Post by jhb1608 on 2009-10-22
Well, will it work on the final OEM release of Windows 7?

---

### Post by ptolomy_was_right on 2009-10-23
> **jhb1608 said:**
> Well, will it work on the final OEM release of Windows 7?
Absolutely. Win 7 final OEM is no prob. I have them running alongside easily. Just follow the instructions at top of thread...

---

### Post by dustoashes on 2009-10-24
Hi,
I've read the entire thread but can't seem  to find the answer to my problem.

I've followed all the steps and after installing Windows 7, re-installed GRUB, etc. But each time I restart, it simply proceeds to Ubuntu.

This is my f-disk l:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       26736   214756888+  83  Linux
/dev/sda2   *       26737       29286    20482875    7  HPFS/NTFS
/dev/sda3           29287       30401     8956237+   5  Extended
/dev/sda5           29287       30401     8956206   82  Linux swap / Solaris
```

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
# kopt=root=UUID=09ac54c0-8e01-4d27-b9f1-87c4ce142c1e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=09ac54c0-8e01-4d27-b9f1-87c4ce142c1e

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

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		09ac54c0-8e01-4d27-b9f1-87c4ce142c1e
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=09ac54c0-8e01-4d27-b9f1-87c4ce142c1e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		09ac54c0-8e01-4d27-b9f1-87c4ce142c1e
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=09ac54c0-8e01-4d27-b9f1-87c4ce142c1e ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		09ac54c0-8e01-4d27-b9f1-87c4ce142c1e
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=09ac54c0-8e01-4d27-b9f1-87c4ce142c1e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		09ac54c0-8e01-4d27-b9f1-87c4ce142c1e
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=09ac54c0-8e01-4d27-b9f1-87c4ce142c1e ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		09ac54c0-8e01-4d27-b9f1-87c4ce142c1e
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=09ac54c0-8e01-4d27-b9f1-87c4ce142c1e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		09ac54c0-8e01-4d27-b9f1-87c4ce142c1e
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=09ac54c0-8e01-4d27-b9f1-87c4ce142c1e ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		09ac54c0-8e01-4d27-b9f1-87c4ce142c1e
kernel		/boot/memtest86+.bin
quiet

title 		windows 7 beta (Loader)
root 		(hd0,1)
savedefault
makeactive
chainloader 	+1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Here I also tried root (hd0,2), though the result doesn't change.

---

### Post by presence1960 on 2009-10-24
> **dustoashes said:**
> Hi,
I've read the entire thread but can't seem  to find the answer to my problem.

I've followed all the steps and after installing Windows 7, re-installed GRUB, etc. But each time I restart, it simply proceeds to Ubuntu.

This is my f-disk l:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       26736   214756888+  83  Linux
/dev/sda2   *       26737       29286    20482875    7  HPFS/NTFS
/dev/sda3           29287       30401     8956237+   5  Extended
/dev/sda5           29287       30401     8956206   82  Linux swap / Solaris
```

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
# kopt=root=UUID=09ac54c0-8e01-4d27-b9f1-87c4ce142c1e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=09ac54c0-8e01-4d27-b9f1-87c4ce142c1e

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

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		09ac54c0-8e01-4d27-b9f1-87c4ce142c1e
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=09ac54c0-8e01-4d27-b9f1-87c4ce142c1e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		09ac54c0-8e01-4d27-b9f1-87c4ce142c1e
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=09ac54c0-8e01-4d27-b9f1-87c4ce142c1e ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		09ac54c0-8e01-4d27-b9f1-87c4ce142c1e
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=09ac54c0-8e01-4d27-b9f1-87c4ce142c1e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		09ac54c0-8e01-4d27-b9f1-87c4ce142c1e
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=09ac54c0-8e01-4d27-b9f1-87c4ce142c1e ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		09ac54c0-8e01-4d27-b9f1-87c4ce142c1e
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=09ac54c0-8e01-4d27-b9f1-87c4ce142c1e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		09ac54c0-8e01-4d27-b9f1-87c4ce142c1e
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=09ac54c0-8e01-4d27-b9f1-87c4ce142c1e ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		09ac54c0-8e01-4d27-b9f1-87c4ce142c1e
kernel		/boot/memtest86+.bin
quiet

title 		windows 7 beta (Loader)
root 		(hd0,1)
savedefault
makeactive
chainloader 	+1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Here I also tried root (hd0,2), though the result doesn't change.

change this :
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
```

to:
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
timeout		[COLOR="Purple"]3[/COLOR]

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Red"]#[/COLOR]hiddenmenu

# Pretty colours
```

Put a # in front of hiddenmenu (in red above) The way you have it now it will not display the GRUB menu unless you hit Esc before the 3 second countdown. For countdown control continue reading.

Set the timeout in seconds to how long to display the GRUB menu before booting the default  which is Ubuntu. (purple above)

---

### Post by dustoashes on 2009-10-25
> **presence1960 said:**
> change this :
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
```

to:
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
timeout		[COLOR="Purple"]3[/COLOR]

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Red"]#[/COLOR]hiddenmenu

# Pretty colours
```

Put a # in front of hiddenmenu (in red above) The way you have it now it will not display the GRUB menu unless you hit Esc before the 3 second countdown. For countdown control continue reading.

Set the timeout in seconds to how long to display the GRUB menu before booting the default  which is Ubuntu. (purple above)

Thanks, works like a charm.

---

### Post by presence1960 on 2009-10-25
> **dustoashes said:**
> Thanks, works like a charm.

Glad you got it like you want it. Enjoy ubuntu.

---

### Post by Grumly666 on 2009-10-26
Pour Win7/Linux Dual Boot, utiliser EasyBCD 2.0 Beta Build65 minimum 
 
[http://neosmart.net/forums/showthread.php?t=642](http://neosmart.net/forums/showthread.php?t=642)[]("http://neosmart.net/forums/showthread.phps=e03ff6ae094ea0de630080114f4a375a&t=642")
 
et suivre intégralement le topic suivant : 
 
[http://doc.ubuntu-fr.org/tutoriel/comment_amorcer_ubuntu_avec_bootmgr#ajout_d_une_entree_de_menu_pour_ubuntu_dans_l_amorceur_de_windows_vista](http://doc.ubuntu-fr.org/tutoriel/comment_amorcer_ubuntu_avec_bootmgr#ajout_d_une_entree_de_menu_pour_ubuntu_dans_l_amorceur_de_windows_vista)

---

### Post by presence1960 on 2009-10-26
> **Grumly666 said:**
> Pour Win7/Linux Dual Boot, utiliser EasyBCD 2.0 Beta Build65 minimum 
 
[http://neosmart.net/forums/showthread.php?t=642](http://neosmart.net/forums/showthread.php?t=642)[]("http://neosmart.net/forums/showthread.phps=e03ff6ae094ea0de630080114f4a375a&t=642")
 
et suivre intégralement le topic suivant : 
 
[http://doc.ubuntu-fr.org/tutoriel/comment_amorcer_ubuntu_avec_bootmgr#ajout_d_une_entree_de_menu_pour_ubuntu_dans_l_amorceur_de_windows_vista](http://doc.ubuntu-fr.org/tutoriel/comment_amorcer_ubuntu_avec_bootmgr#ajout_d_une_entree_de_menu_pour_ubuntu_dans_l_amorceur_de_windows_vista)

EasyBCD is crap in my opinion. GRUB works better and is way more customisable. But to each his/her own.

---

### Post by CrownRU on 2009-10-27
With Win 7 & Ubuntu 9.10 (grub2) is the same solution as with grub (1) ?

---

### Post by hyperdude111 on 2009-10-27
> **CrownRU said:**
> With Win 7 & Ubuntu 9.10 (grub2) is the same solution as with grub (1) ?

No, grub two is entirely different. When I get time I will add a section for grub two, but for now try searching in google.

---

### Post by presence1960 on 2009-10-27
> **hyperdude111 said:**
> No, grub two is entirely different. When I get time I will add a section for grub two, but for now try searching in google.

[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)

---

### Post by topgun_tapan on 2009-11-01
I installed ubuntu 9.10 first and then installed Windows 7. After that i followed the tutorial [here]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD") to reinstall grub. After i ran the command *update-grub*, it detected Windows 7 automatically and added it to the grub.cfg file. However, now when I try to start windows from the grub, It doesn't load windows and instead just shows the grub again after a second. Here is my *fdisk -l*
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x597e5e85

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4255    34178256   83  Linux
/dev/sda2            4256        4379      996030    5  Extended
/dev/sda3   *        4380       14593    82043955    7  HPFS/NTFS
/dev/sda5            4256        4379      995998+  82  Linux swap / Solaris
```and here is my *grub.cfg* file
```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set fa42374d-e7b7-4877-848f-f9d80985c641
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set fa42374d-e7b7-4877-848f-f9d80985c641
insmod tga
if background_image /usr/share/images/grub/splash.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set fa42374d-e7b7-4877-848f-f9d80985c641
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=fa42374d-e7b7-4877-848f-f9d80985c641 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set fa42374d-e7b7-4877-848f-f9d80985c641
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=fa42374d-e7b7-4877-848f-f9d80985c641 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set f0107bd3107b9f72
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```

---

### Post by hyperdude111 on 2009-11-01
> set root=(hd0,3)

Is that the correct partition you have windows 7 on ?

---

### Post by chessplayer on 2009-11-03
This is in reply to the very first post in this thread by hyperdude111 and following the link provided by presence1960:

Hyperdude111 wrote the following "algorithm":

1.	Obtain a copy of Windows7.
2.	Partition your disk with gparted.
3.	Install Windows7.
4.	Re-install Grub.
5.	Edit Grub to List Windows 7.
6.	Have Fun.

The point is that points 4 and 5 can now (i.e. with 9.10 (karmic)) be done automatically, if you have a live CD or USB-Stick!

Step 4 becomes booting from live device and following [http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD")

Step 5 then just needs booting the installed ubuntu and doing what [http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-mkconfig]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#grub-mkconfig")  has to say

The "Have fun" part stays the same!

---

### Post by sqeeeksLongboards on 2009-11-16
I have an issue with this... I've tried two things:
-Installing windows 7 first, then ubuntu on a different partition, grub finds Win7 fine, but it won't boot. I select Win7 and it restarts. 
-Same as above, but with different hard drives
-Ubuntu first, then 7, as soon as I add 7 to grub, it won't boot. Any help? *sigh* i'm on a school computer right now, i'll add my .cfg to this when I get home...

---

### Post by hyperdude111 on 2009-11-16
> **sqeeeksLongboards said:**
> I have an issue with this... I've tried two things:
-Installing windows 7 first, then ubuntu on a different partition, grub finds Win7 fine, but it won't boot. I select Win7 and it restarts. 
-Same as above, but with different hard drives
-Ubuntu first, then 7, as soon as I add 7 to grub, it won't boot. Any help? *sigh* i'm on a school computer right now, i'll add my .cfg to this when I get home...

Are you on ubuntu 9.04 or 9.10 ?

---

### Post by sqeeeksLongboards on 2009-11-18
> **hyperdude111 said:**
> Are you on ubuntu 9.04 or 9.10 ?
i'm on 9.10. My latest attempt is:
-Win7 Installed and working on 1st hard drive
-Installed 9.10 on second hard drive
-attempting to edit grub to display 7
My new problem is that I can run the grub-mkconfig command fine, but when I use the -o tag it doesn't seem to put the file into /boot/grub/ or anywhere else... it just doesn't exist... had this problem with xorg.conf - is everyone just getting rid of config files? I mean, being a Windows guy, I'm kind of glad the config files are dissapearing, but I think they should have an alternative to them _before_ they get rid of the file... *sigh* idk. Whatever. I'll shut up now...

---

### Post by sqeeeksLongboards on 2009-11-19
I think I figured out what was going on-
Ubuntu couldn't see the first 20mb or so of my drive, for some reason. 
Windows could. Windows loader installed on the first 100mb
GRUB installer couldn't see the partition with the windows loader on it, so it installed grub over it, thinking the first 80mb was empty... or something like that. I'm gonna try partitioning with live CD, then installing 7, then installing Ubuntu... *sigh* i'm tired... yaay for forums... ttyl

---

### Post by harvillionare on 2009-11-20
I got to step 4 and when i booted using live flash drive I put in
> sudo grubwhich it replied with:
> command not foundI then followed the second part on this website [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) about mounting the drive.  But still when i get to the sudo grub step i get the command not found error. I then typed > sudo apt-get install gruband it said it didnt need to be installed because it had grub-pc.. 
I tried it another time and it installed..
The grub folder on the partition that contains ubuntu only has a grubenv file, both before and after i installed grub? Any help would be appreciated.

---

### Post by FLnola on 2009-11-20
Hello, is there a thread available for Windows7 (installed first)? I have been reading about Ubuntu, and I want to add it to my Windows7 netbook. Any help would be greatly appreciated.

---

### Post by McGuffin on 2009-11-22
> **FLnola said:**
> Hello, is there a thread available for Windows7 (installed first)? I have been reading about Ubuntu, and I want to add it to my Windows7 netbook. Any help would be greatly appreciated.

I'm also in a similar position, though I understand that it's best to set up drive partitions using the windows partitioning tools?  Is this the case?  If so, how do I go about doing it?

Thanks

McG.

---

### Post by FLnola on 2009-11-22
You can find the Windows 7 Partition manager, if you enter partition in the search if you type in partition. You can create the partition there. You will also need to make the partition a simple volume. PM me and Let me know how it goes.

---

### Post by W A L E E D on 2009-11-23
Thanx so much to hyperdude111 and presence1960.

---

### Post by hyperdude111 on 2009-11-24
For windows 7 installed first it is best to use the Win7 partitioning tools, gparted and others for some reason cause boot issues with win7.

---

### Post by presence1960 on 2009-11-24
> **hyperdude111 said:**
> For windows 7 installed first it is best to use the Win7 partitioning tools, gparted and others for some reason cause boot issues with win7.

+1

Windows 7 is basically Vista cleaned up. Vista has the same problem when resizing Vista's partition with anything other than it's own disk management utility. Here is a [link]("http://bugzilla.gnome.org/show_bug.cgi?id=379482") to the as yet unresolved bug.

---

### Post by Junkieman on 2009-11-25
Great Howto! I have a different setup, and have some questions if anyone here has some answers, Ill be very grateful :)

- I'm running Intrepid 8.10 on SATA0 (sda)
- Have a storage drive on SATA1 (sdb)

I want to install Windows 7 on a *new drive*, preferably with the other drives disconnected, and after wards I will connect everything up and edit my GRUB config to include the new drive.

**The questions**

- If I connect the new drive to SATA2, will GRUB be able to boot it, since it's further down the chain than SATA0/1? 

- And if it can't, will swapping the new drive with my storage drive change the device assignments in Ubuntu? i.e. Storage sdb will become sdc. In this case, are there any caveats or manual changes I should know about, apart from editing fstab to point to the new storage drive sdc?

---

### Post by richdf on 2009-11-25
[FONT="Tahoma"]Thanks for the excellent How-To. :D

I did have Win 7 & Jaunty as a dual boot, but after removing Win 7 & having major reinstall issues, I decided to try solo Ubuntu (with XP in VBox for those annoying IE specific sites, namely Outlook Web Access!)

45 of tinkering last night & I now have Win 7 & Ubuntu dual again. Although I am an old skool M$ admin, I am loving Linux, but it doesn't hurt to have a spare OS for when (not if) I mess things up!!:oops:[/FONT]

---

### Post by Freesprt30 on 2009-11-28
Thanks for this great How-TO.

  I have a question to make sure I read all these post right.  I am getting win 7 on Monday.  I currently have xp and unbuntu dual boot.  I have xp on partition 1 and ubuntu on part 2 with 3rd partition  being the largest partition where I save all my files from either OS. ( so I can destroy either OS and not loose anything).

   On the first post I read where ubuntu needs to be on the first partition for grub to work.  Here is my question.  Should I remove both OS's and install ubuntu on the first partition before I install WIn 7?

Thanks

---

### Post by presence1960 on 2009-11-28
> **Freesprt30 said:**
> Thanks for this great How-TO.

  I have a question to make sure I read all these post right.  I am getting win 7 on Monday.  I currently have xp and unbuntu dual boot.  I have xp on partition 1 and ubuntu on part 2 with 3rd partition  being the largest partition where I save all my files from either OS. ( so I can destroy either OS and not loose anything).

   On the first post I read where ubuntu needs to be on the first partition for grub to work.  Here is my question.  Should I remove both OS's and install ubuntu on the first partition before I install WIn 7?

Thanks

Ubuntu does not have to be on the first partition to work. GRUB usually goes on the MBR which is not a partition. My Ubuntu 9.04 is on sda6 inside sda2 (extended partition) and Ubuntu 9.10 is on sda7 inside sda2. sda6 & sda7 are logical partitions.

As far as windows it needs to be on a primary partition unless you install a second version which the OS will take care of that one. it will put the new windows on a logical partition and combine bootloading with the first windows OS.

---

### Post by Freesprt30 on 2009-11-29
presence1960 

    Thank you for your quick response. That answered my question.

---

### Post by iamfreeman on 2009-12-02
i have an hp dv-7 series laptop. i installed a 320gb hdd to complement the 500gb hdd they provided. i installed ubuntu on the 320gb hdd, and then a few days later i installed win7 enterprise from win7 ultimate, of course giving it the 500gb hdd. i also formatted the hp recovery partition.the 320gb hdd only reads 149gb
and the  dual boot option is unavailable. at this point i want to get ubuntu off my laptop as i am going to purchase another one solely for ubuntu. the problem is that ubuntu has gone awol along with 149gb of hdd. HOW THE HELL DO I RECOVER MY HDD AND DELETE UBUNTU????:popcorn:

---

### Post by Junkieman on 2009-12-03
> **iamfreeman said:**
> i have an hp dv-7 series laptop. i installed a 320gb hdd to complement the 500gb hdd they provided. i installed ubuntu on the 320gb hdd, and then a few days later i installed win7 enterprise from win7 ultimate, of course giving it the 500gb hdd. i also formatted the hp recovery partition.the 320gb hdd only reads 149gb
and the  dual boot option is unavailable. at this point i want to get ubuntu off my laptop as i am going to purchase another one solely for ubuntu. the problem is that ubuntu has gone awol along with 149gb of hdd. HOW THE HELL DO I RECOVER MY HDD AND DELETE UBUNTU????:popcorn:
Freeman, you can boot the Ubuntu Live CD and from there you have two options:

- [Resintall GRUB (Point #12) ]("http://ubuntuforums.org/showthread.php?t=1195275")so that you can choose between Ubuntu or Windows when you boot.

- Use Admin -> Partition Editor to format/resize the partition and reclaim that space.

Judging by the copious amount of punctuation you use, here's a tip when working with partitions: read the instructions carefully; check and double-check what you are doing; backup your important files.

---

### Post by iamfreeman on 2009-12-04
thank you junkieman. i will try this and let you know the result. i have previously tried to install the grub loader but it failed. i tried to load the cd but it only offers to install with wubi, which is not the original install procedure. i am re-downloading the live cd and will try again as soon as it is done. thank you for your help as i am very new to this. i am very interested in learning, as i see it as a way to advance my now pitiful knowledge of ubuntu and the linux community

---

### Post by iamfreeman on 2009-12-05
i used gparted and formatted the whole 320gb hdd, upon reboot i was worried that i screwed something up when windows was not showing the drive. then i remembered that it was a raw drive so i used windows disk management, and fixed the issue. now i have the whole 320gb drive in one piece. so i got froggy and tried to reintegrate the 14gb partition hp uses for recovery back into the 500gb drive to create one partition there. unfortunately it did not work. the recovery partition is empty as i originally purchased the laptop with vista and have upgraded. is it possible to merge the two partitions or would i have to reinstall the os? also what is the best site for e-books on ubuntu (free of course).

---

### Post by Junkieman on 2009-12-06
> **iamfreeman said:**
> now i have the whole 320gb drive in one piece. 
So you solved your original issue then.

> **iamfreeman said:**
> tried to reintegrate the 14gb partition hp uses for recovery back into the 500gb drive to create one partition there
This is a different issue now? Hmm I would've said leave the recovery partition, it's there for a reason, especially for the OS that needs it ;) This is beyond this topic's scope, [this topic is more suited for this particular issue.]("http://ubuntuforums.org/showthread.php?t=941624")

---

### Post by Freesprt30 on 2009-12-12
Thanks again for the great post.

   I just installed Win 7 Professional.  I didn't have to do all the steps, this is what I did with my configuration.

  I had WInXP on HD0,0  a 200G Partition called Shared on hd0,1 and Unbuntu on hd0,4  and of course swap and stuff

 1. I installed win7 on hd0,0 were XP was.
 2. I booted to live Ubuntu CD and followed step4 (re-Install Grub)from 1st post. 
 3. When I rebooted I saw the WinXP home was there so I said what the hell. 
 4. I selected WINXP without ever booting in to Ubuntu and I got into win7 No Prob.
 5.  I restarted and booted into Ubuntu with no Problem.  I looked at step 5 but decided I can boot to both so why change anything.

   The only problem I saw that I will have to go look at.  Is when I was in Ubuntu for the 4 min or so.  I tried to access my Shared drive.  It asked for authentication as normal, however it would not except my pass word.  
 DO I need to unmount and remount?

 Also should I edit grub/menu.lst to show Win7 instead of "windows XP Home Edition"


  Thanks again for the great post.

---

### Post by Ralphie on 2009-12-15
I have been having issues with this.
It seems like if the installer simply *sees* any partition not made with the windows partition editor, it will not install. Even if that specific partition was made with the windows editor. 

In one machine I disconnected all other HDDs (Ubuntu on one, Snow Leopard OSX on the other), and I was able to install flawlessly to the third HDD. 

On the machine I am trying to install to now, I only have one HDD, partitioned for ubuntu/windows, and it doesn't like it. I don't know what to do, it's not like I can just turn off the ubuntu partition to make windows happy for the install. 

Any ideas?
Thanks in advance!

---

### Post by phillychease on 2009-12-17
very good!

---

### Post by rlvarcoe on 2009-12-21
Great thread, I tried the above with windows 7 installed and got to the grub> root >(hdx,y) and it kept giving me an unrecognized command message.  So I skipped the step and just entered setup (hd0)!  then quit... to my suprise I rebooted and my old grub menu was in place.  Note I did not do anything beyond the setup (hd,0) including the gedit boot/grub nor did I have to add the lines to the menu.lst.  Go figure!

---

### Post by ignatiusmael on 2009-12-22
Hi,
Thanks for a great tutorial to dual-boot XP and Ubuntu! All went well with the install, then tried to change boot sequence to make Windows XP default, removed 'saveddefault' from Ubuntu, but did not work, still wanted to boot Ubuntu first. Tried to go back into the terminal to see if I missed something, but now it will not allow me to put the password in, I can type in sudo gedit /boot/grub/menu.lst no problems, and it worked before, so what has happened?hope you can help,want to learn Linux so can ultimately get rid of Windows!'thanks

---

### Post by hyperdude111 on 2009-12-22
> **ignatiusmael said:**
> Hi,
Thanks for a great tutorial to dual-boot XP and Ubuntu! All went well with the install, then tried to change boot sequence to make Windows XP default, removed 'saveddefault' from Ubuntu, but did not work, still wanted to boot Ubuntu first. Tried to go back into the terminal to see if I missed something, but now it will not allow me to put the password in, I can type in sudo gedit /boot/grub/menu.lst no problems, and it worked before, so what has happened?hope you can help,want to learn Linux so can ultimately get rid of Windows!'thanks

In terminal you can not see the password you input, however it is still being read by the OS. It's just a security precaution it should work.

If not press Alt+F2 and type "gksu nautilus". Then navigate through boot-grub and open menu.lst and configure from there.

---

### Post by havoc783 on 2009-12-23
Hi, thanks for the tutorial.  I installed Windows 7 successfully and attempted to restore the grub using the latest version of the Ubuntu live CD. For one, grub is not installed. No biggie though, because I just apt-get install it. After that,  I run grub and the find /boot... command and I get the hd1,0. I enter the information as shown, quit grub and reboot and it automatically boots into my Windows 7 partition again.  What am I doing wrong?

---

### Post by hyperdude111 on 2009-12-23
> **havoc783 said:**
> Hi, thanks for the tutorial.  I installed Windows 7 successfully and attempted to restore the grub using the latest version of the Ubuntu live CD. For one, grub is not installed. No biggie though, because I just apt-get install it. After that,  I run grub and the find /boot... command and I get the hd1,0. I enter the information as shown, quit grub and reboot and it automatically boots into my Windows 7 partition again.  What am I doing wrong?

Try hd0,1 not 1,0

---

### Post by presence1960 on 2009-12-23
> **havoc783 said:**
> Hi, thanks for the tutorial.  I installed Windows 7 successfully and attempted to restore the grub using the latest version of the Ubuntu live CD. For one, grub is not installed. No biggie though, because I just apt-get install it. After that,  I run grub and the find /boot... command and I get the hd1,0. I enter the information as shown, quit grub and reboot and it automatically boots into my Windows 7 partition again.  What am I doing wrong?

Don't just guess putting in stuff! Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by hyperdude111 on 2009-12-24
> **marmel said:**
> Hi hyperdude111,

Thanks for the guide! Unfortunately it didn't work for me... :( When I boot Windows 7 via grub the system resets after trying to load Windows and no error message is displayed. I am sure that the partition number in the grub entry is correct (sda1 -> hd0,0).

Any suggestion?

Thank you so much!

If the system just resets without any message or logo from Win7 the wrong partition is most likely.

If it is the correct partition and is starts to semi-load then fails it is probably a bad install.

---

### Post by americaeh on 2009-12-24
thank you this is the fourth or fith time i'm using this guide. Its a real help but sometimes i have to type: sudo apt-get install grup first

---

### Post by havoc783 on 2009-12-28
> **presence1960 said:**
> Don't just guess putting in stuff! Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

I ran that script and the saw that the ubuntu partition is on (hd1,0). I installed grub again and typed the root (hd1,0) and it came back with a string unrecognized device string (Error 11).

Does it need to be mounted first?

---

### Post by presence1960 on 2009-12-28
> **havoc783 said:**
> I ran that script and the saw that the ubuntu partition is on (hd1,0). I installed grub again and typed the root (hd1,0) and it came back with a string unrecognized device string (Error 11).

Does it need to be mounted first?

I need the info from the output of the script before I can answer anything. Post the contents of the RESULTS.txt file here please. Remember the whole reason I asked you to download & run the script is so we won't be guessing.

---

### Post by keypox on 2009-12-31
I have nothing but issues with grub 2.

After installing windows, after ubuntu.  Booting from ubuntu 9.10 live disk
In terminal

ubuntu@ubuntu:~$ sudo grub
sudo: grub: command not found

and

ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# grub
The program 'grub' is currently not installed.  You can install it by typing:
apt-get install grub
grub: command not found
root@ubuntu:~#

I believe these directions will work though [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Restoring%20GRUB](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Restoring%20GRUB)

---

### Post by presence1960 on 2009-12-31
> **keypox said:**
> I have nothing but issues with grub 2.

After installing windows, after ubuntu.  Booting from ubuntu 9.10 live disk
In terminal

ubuntu@ubuntu:~$ sudo grub
sudo: grub: command not found

and

ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# grub
The program 'grub' is currently not installed.  You can install it by typing:
apt-get install grub
grub: command not found
root@ubuntu:~#

I believe these directions will work though [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Restoring%20GRUB](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Restoring%20GRUB)

That info is really to generalized to see what is actually going on with your setup & boot process. We need more detailed, specific info. 

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by havoc783 on 2010-01-07
> **presence1960 said:**
> That info is really to generalized to see what is actually going on with your setup & boot process. We need more detailed, specific info. 

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Here is the RESULT file:
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcab10bee

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   469,852,159   469,645,312   7 HPFS/NTFS
/dev/sda3         469,853,055   488,392,064    18,539,010   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00068ec9

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   964,992,419   964,992,357  83 Linux
/dev/sdb2         964,992,420   976,768,064    11,775,645   5 Extended
/dev/sdb5         964,992,483   976,768,064    11,775,582  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="1A0CD2FB0CD2D13D" LABEL="System Reserved" TYPE="ntfs" 
sda2: UUID="86BCEBF1BCEBDA27" TYPE="ntfs" 
sda3: LABEL="HP_RECOVERY" UUID="4B6E-6BC0" TYPE="vfat" 
sdb1: UUID="35aca799-605c-46a3-b338-27b3edcf2813" SEC_TYPE="ext2" TYPE="ext3" 
sdb5: UUID="9531ff06-27df-45ff-842b-a981670b098b" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda3/boot.ini: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


================================ sda3/BOOT.INI: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 9.04, kernel 2.6.28-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, kernel 2.6.24-21-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 9.04, kernel 2.6.22-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.22-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro  single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 9.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=35aca799-605c-46a3-b338-27b3edcf2813 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sdb5
UUID=9531ff06-27df-45ff-842b-a981670b098b none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.22-15-generic
    .0GB: boot/initrd.img-2.6.22-15-generic.bak
    .0GB: boot/initrd.img-2.6.24-21-generic
    .0GB: boot/initrd.img-2.6.24-21-generic.bak
    .0GB: boot/initrd.img-2.6.27-14-generic
    .0GB: boot/initrd.img-2.6.28-11-generic
    .0GB: boot/initrd.img-2.6.28-13-generic
    .0GB: boot/initrd.img-2.6.28-14-generic
    .0GB: boot/initrd.img-2.6.28-15-generic
    .0GB: boot/initrd.img-2.6.28-16-generic
    .0GB: boot/vmlinuz-2.6.22-15-generic
    .0GB: boot/vmlinuz-2.6.24-21-generic
    .0GB: boot/vmlinuz-2.6.27-14-generic
    .0GB: boot/vmlinuz-2.6.28-11-generic
    .0GB: boot/vmlinuz-2.6.28-13-generic
    .0GB: boot/vmlinuz-2.6.28-14-generic
    .0GB: boot/vmlinuz-2.6.28-15-generic
    .0GB: boot/vmlinuz-2.6.28-16-generic
    .0GB: grub/stage2
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg sdh

---

### Post by presence1960 on 2010-01-07
> **havoc783 said:**
> Here is the RESULT file:
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcab10bee

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   469,852,159   469,645,312   7 HPFS/NTFS
/dev/sda3         469,853,055   488,392,064    18,539,010   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00068ec9

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   964,992,419   964,992,357  83 Linux
/dev/sdb2         964,992,420   976,768,064    11,775,645   5 Extended
/dev/sdb5         964,992,483   976,768,064    11,775,582  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="1A0CD2FB0CD2D13D" LABEL="System Reserved" TYPE="ntfs" 
sda2: UUID="86BCEBF1BCEBDA27" TYPE="ntfs" 
sda3: LABEL="HP_RECOVERY" UUID="4B6E-6BC0" TYPE="vfat" 
sdb1: UUID="35aca799-605c-46a3-b338-27b3edcf2813" SEC_TYPE="ext2" TYPE="ext3" 
sdb5: UUID="9531ff06-27df-45ff-842b-a981670b098b" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda3/boot.ini: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


================================ sda3/BOOT.INI: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 9.04, kernel 2.6.28-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, kernel 2.6.24-21-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 9.04, kernel 2.6.22-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.22-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro  single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 9.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=35aca799-605c-46a3-b338-27b3edcf2813 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sdb5
UUID=9531ff06-27df-45ff-842b-a981670b098b none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.22-15-generic
    .0GB: boot/initrd.img-2.6.22-15-generic.bak
    .0GB: boot/initrd.img-2.6.24-21-generic
    .0GB: boot/initrd.img-2.6.24-21-generic.bak
    .0GB: boot/initrd.img-2.6.27-14-generic
    .0GB: boot/initrd.img-2.6.28-11-generic
    .0GB: boot/initrd.img-2.6.28-13-generic
    .0GB: boot/initrd.img-2.6.28-14-generic
    .0GB: boot/initrd.img-2.6.28-15-generic
    .0GB: boot/initrd.img-2.6.28-16-generic
    .0GB: boot/vmlinuz-2.6.22-15-generic
    .0GB: boot/vmlinuz-2.6.24-21-generic
    .0GB: boot/vmlinuz-2.6.27-14-generic
    .0GB: boot/vmlinuz-2.6.28-11-generic
    .0GB: boot/vmlinuz-2.6.28-13-generic
    .0GB: boot/vmlinuz-2.6.28-14-generic
    .0GB: boot/vmlinuz-2.6.28-15-generic
    .0GB: boot/vmlinuz-2.6.28-16-generic
    .0GB: grub/stage2
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg sdh
```

You do not have GRUB2, you have Legacy GRUB 0.97. You also do not have 9.10- you have 9.04 installed on sdb1. You need to do two things: make sdb (500 GB) disk first in the hard disk boot order in BIOS so GRUB will take over when you boot. Then you need to change the (hd1,0) designations in the kernel stanzas of menu.lst to (hd0,0) since that sdb disk will now be booting first.

So boot your machine and go into BIOS. In the hard disk boot order set the 500 GB (sdb) to boot first before the 250 GB (sda). Save changes to CMOS and continue booting. Highlight Ubuntu at the GRUB menu and hit "e" to edit that kernel. Using your arrow keys navigate to the (hd1,0) designation and change it to (hd0,0). Then hit Ctrl + x to boot. This should boot you into Ubuntu. When the desktop loads open a terminal (Applications > Accessories > Terminal) and run this command ```
gksu gedit /boot/grub/menu.lst
```
that is a lowercase L in .lst

Scroll down to the Ubuntu kernels section and change this in red:


```
title		Ubuntu 9.04, kernel 2.6.28-16-generic
[COLOR="Red"]root		(hd1,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
[COLOR="Red"]root		(hd1,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
[COLOR="Red"]root		(hd1,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
[COLOR="Red"]root		(hd1,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic
```

TO:

```
title		Ubuntu 9.04, kernel 2.6.28-16-generic
[COLOR="Red"]root		(hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
[COLOR="Red"]root		(hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
[COLOR="Red"]root		(hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
[COLOR="Red"]root		(hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=35aca799-605c-46a3-b338-27b3edcf2813 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic
```

Remove the other kernel entries as you only need two kernels and except for the next two they are not 9.04 kernels and are not needed. 

Now scroll down to the windows entries. Change this:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

TO:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows 7 
rootnoverify    (hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1

```

Click Save on top toolbar and close file.

Now you can uninstall those unneeded kernels if you wish (not necessary) by going to System > Administration > Synaptic Package Manager.

Tick for complete removal the following:

linux-image-2.6.28-14
linux-image-2.6.28-13
linux-image-2.6.28-11
linux-image-2.6.27-14
linux-image-2.6.24-21
linux-image-2.6.22-15

 &

linux-headers-2.6.28-14
linux-headers-2.6.28-13
linux-headers-2.6.28-11
linux-headers-2.6.27-14
linux-headers-2.6.24-21
linux-headers-2.6.22-15

Click Apply and that will uninstall and remove those kernel packages that are not needed.

---

### Post by Dananjaya86 on 2010-01-12
Thanks a lot for this tutorial hyperdude111. but I have a problem. i followed the tutorial step-by-step as you specified, and Everything worked fine until where in the GRUB menu, you get to choose which OS to boot. When i choose Windows 7 the machine just restarts and When i Choose Ubuntu it boots Ubuntu with No problems at all. This is my menu.lst file;
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
# kopt=root=UUID=18b1dcd5-0426-4c76-942c-1a740b7fc2a2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=18b1dcd5-0426-4c76-942c-1a740b7fc2a2

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

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		18b1dcd5-0426-4c76-942c-1a740b7fc2a2
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=18b1dcd5-0426-4c76-942c-1a740b7fc2a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		18b1dcd5-0426-4c76-942c-1a740b7fc2a2
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=18b1dcd5-0426-4c76-942c-1a740b7fc2a2 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		18b1dcd5-0426-4c76-942c-1a740b7fc2a2
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=18b1dcd5-0426-4c76-942c-1a740b7fc2a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		18b1dcd5-0426-4c76-942c-1a740b7fc2a2
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=18b1dcd5-0426-4c76-942c-1a740b7fc2a2 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, memtest86+
uuid		18b1dcd5-0426-4c76-942c-1a740b7fc2a2
kernel		/boot/memtest86+.bin
quiet

title	 Windows 7 (Loader)
root	 (hd0,1)
savedefault
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

```

also after going through lots of threads i found this [_little script_]("http://sourceforge.net/projects/bootinfoscript/") and the output i get after running that is this,
```

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90909090

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    74,541,599    74,541,537  83 Linux
/dev/sda2    *     74,541,600   153,372,554    78,830,955   7 HPFS/NTFS
/dev/sda3         153,372,555   156,296,384     2,923,830   5 Extended
/dev/sda5         153,372,618   156,296,384     2,923,767  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="18b1dcd5-0426-4c76-942c-1a740b7fc2a2" TYPE="ext3" 
sda2: UUID="D680D88480D86C8D" TYPE="ntfs" 
sda5: UUID="ca1547f4-d586-45d6-9b69-ccddd7fd88bb" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dananjaya/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dananjaya)
/dev/sr2 on /media/Mobile Partner   type iso9660 (ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=18b1dcd5-0426-4c76-942c-1a740b7fc2a2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=18b1dcd5-0426-4c76-942c-1a740b7fc2a2

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

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		18b1dcd5-0426-4c76-942c-1a740b7fc2a2
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=18b1dcd5-0426-4c76-942c-1a740b7fc2a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		18b1dcd5-0426-4c76-942c-1a740b7fc2a2
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=18b1dcd5-0426-4c76-942c-1a740b7fc2a2 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		18b1dcd5-0426-4c76-942c-1a740b7fc2a2
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=18b1dcd5-0426-4c76-942c-1a740b7fc2a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		18b1dcd5-0426-4c76-942c-1a740b7fc2a2
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=18b1dcd5-0426-4c76-942c-1a740b7fc2a2 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, memtest86+
uuid		18b1dcd5-0426-4c76-942c-1a740b7fc2a2
kernel		/boot/memtest86+.bin
quiet

title	 Windows 7 (Loader)
root	 (hd0,1)
savedefault
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=18b1dcd5-0426-4c76-942c-1a740b7fc2a2 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ca1547f4-d586-45d6-9b69-ccddd7fd88bb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.31-15-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-15-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

Can anyone please help me to figure this out? oh..and I'm sorry if i haven't provided adequate information. These are the info i thought that would be useful in solving this problem.

---

### Post by Hate on 2010-01-16
Hi,
I've got a problem following the procedure in the first post, when I boot ubuntu live cd to get grub to work again using

```
sudo grub
```

It returns command not found

EDIT: it's that because of 9.10 ? Should I have to install grub manually from livecd terminal ?

---

### Post by perspectoff on 2010-01-16
Gparted doesn't work if Windows 7 is already installed.

While 2 operating systems on a hard drive is not so difficult, what if you want more than 2?

For a thorough guide that allows for chainloading of any type of OS (or many OS on a single hard drive), see

[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

at Ubuntuguide.org

---

### Post by Dananjaya86 on 2010-01-17
I got both OS's to work in the following way. Configure your Hard drive to any layout you like using Gparted and Install Windows 7 in the NTFS Partition. After that Put on an Ubuntu Live CD, boot to it, open a terminal and type following Commands.
```

sudo grub

find /boot/grub/stage1

root (hdX,Y)
setup (hdX,Y)
setup (hdX,Y)
quit

```Note: The letters X and Y in above commands will depend on the output of
```
find /boot/grub/stage1
```Also i have delibarately typed the ```
setup (hdX,Y)
``` command twice.

After that restart the machine and boot back in to Windows 7. Install the software _[EasyBCD]("http://neosmart.net/dl.php?id=1")_.
follow the instructions _[here]("http://neosmart.net/wiki/display/EBCD/Ubuntu")_ to learn how to insert Ubuntu to it's Bootloader and after everything is completed, restart your machine and you should be able to access both operating systems without hassle.

---

### Post by whistlerspa on 2010-01-21
> **Dananjaya86 said:**
> I got both OS's to work in the following way. Configure your Hard drive to any layout you like using Gparted and Install Windows 7 in the NTFS Partition. After that Put on an Ubuntu Live CD, boot to it, open a terminal and type following Commands.
```

sudo grub

find /boot/grub/stage1

root (hdX,Y)
setup (hdX,Y)
setup (hdX,Y)
quit

```Note: The letters X and Y in above commands will depend on the output of
```
find /boot/grub/stage1
```Also i have delibarately typed the ```
setup (hdX,Y)
``` command twice.

After that restart the machine and boot back in to Windows 7. Install the software _[EasyBCD]("http://neosmart.net/dl.php?id=1")_.
follow the instructions _[here]("http://neosmart.net/wiki/display/EBCD/Ubuntu")_ to learn how to insert Ubuntu to it's Bootloader and after everything is completed, restart your machine and you should be able to access both operating systems without hassle.

None of this worked for me just get a file not found error:(

---

### Post by presence1960 on 2010-01-21
> **whistlerspa said:**
> None of this worked for me just get a file not found error:(

That is because those commands are for legacy GRUB. You probably have GRUB2. We need very detailed info about your setup & boot process to troubleshoot for you. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

You do not need Easy BCD to dual boot. GRUB is better and more configurable anyway. GRUB is all you need.

---

### Post by ptolomy_was_right on 2010-01-26
> **easybake said:**
> I've only ran into problems with it. It's much easier done from a Mac base. Then you would just boot camp and use Refit. Done and Done. 

But with mac's they use the Darwin bootloader which can be a huge pain in the ***. If you get any luck with it please let me know. I think I was trying it with a Kalyway OSX 86 disc. You might have better luck than I did.

I never got past "HFS+ parition error"

Taken me three freakin' months, but yeah, **finally** I'm running Win 7 Ultimate alongside OS X Leopard 10.5.7 on my VAIO laptop. Using the awesome Boot Think loader (the only one practically that doesn't auto-default one OS or the other). Leopard is running v smooth but it's taken some fiddling about with kexts etc. Managed to get 'em both on MBR which helped with the dual boot (windows being a control freak). Woohoo! Loving this....:D

---

### Post by PJMRK on 2010-02-05
thanks for the tutorial, works for installing windows first too.

---

### Post by lastelement on 2010-02-15
OK I'm having an issue after Windows 7 is installed. 

I can dual boot both Ubuntu and Windows 7 and switch back and forth, UNTIL I run the activator for my illegit Windows 7. At that point, booting to 7 gets the blinking _ cursor that hangs.

However, for example, if I have Ubuntu installed first, install Windows 7, run the activator, then the problem occurs. So its happens even without reinstalling GRUB.

I've used two different Windows 7 images, and 3 different activator programs. Re-installed Windows more times than someone ever should. So I'm guessing the issue must be with the order of my hard drive partitions. Here's what I got.

sda1 - NTFS (just data)
sdb1 - NTFS (Windows 7) (flag "boot")
sdb2 - ext3 (Ubuntu)
sdb3 - swap
sdb4 - NTFS (extra space)

Before trying to install Windows 7, I had Windows XP installed on sdb1 and dual-booted for a while with no problems. 

Thanks for any help, I appreciate this guide.

---

### Post by presence1960 on 2010-02-15
> **lastelement said:**
> OK I'm having an issue after Windows 7 is installed. 

I can dual boot both Ubuntu and Windows 7 and switch back and forth, UNTIL I run the activator for my illegit Windows 7. At that point, booting to 7 gets the blinking _ cursor that hangs.

However, for example, if I have Ubuntu installed first, install Windows 7, run the activator, then the problem occurs. So its happens even without reinstalling GRUB.

I've used two different Windows 7 images, and 3 different activator programs. Re-installed Windows more times than someone ever should. So I'm guessing the issue must be with the order of my hard drive partitions. Here's what I got.

sda1 - NTFS (just data)
sdb1 - NTFS (Windows 7) (flag "boot")
sdb2 - ext3 (Ubuntu)
sdb3 - swap
sdb4 - NTFS (extra space)

Before trying to install Windows 7, I had Windows XP installed on sdb1 and dual-booted for a while with no problems. 

Thanks for any help, I appreciate this guide.

You had better seek advice from whom you got that pirated software. This community stands firm in it's opposition to illegal/pirated software. My advice: stay away from pirated software-period!

---

### Post by wilee-nilee on 2010-02-15
> **presence1960 said:**
> You had better seek advice from whom you got that pirated software. This community stands firm in it's opposition to illegal/pirated software. My advice: stay away from pirated software-period!

Also in the next day or so the MS updates will contain....
[http://www.sevenforums.com/windows-update/63126-windows-activation-technologies-update-windows-7-a.html](http://www.sevenforums.com/windows-update/63126-windows-activation-technologies-update-windows-7-a.html)

---

### Post by littlepeon on 2010-02-20
hey....

quick note....Karmic does not use regular grub....Karmic uses Grub2

when you install win7/vista/xp/win-whatever on an existing ubuntu 9.10 you will wipe out grub (windows takes over your boot-loader automatically)

you will then have to reinstall grub (and might have to edit grub to point to your windows install)

the 'normal' reinstall grub instructions (the ones that point to 'look for grub/stage1....or the ones that say 'look for grub menu.list) will NOT work....Grub 2 is a new/different beast..

am not on my ubuntu machine...so i cannot give the howto...but there are many here on how to reinstall Grub 2 and that is what u will have to do...

have fun 
-peon

---

### Post by Dfairlite on 2010-02-28
Ok I have been trying the whole weekend to do this. I have scoured the forums and tried every solution i came across but can't get this to work.if someone would please help me i would really appreciate it.
here is the output of fdisk -l:

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d7f4c9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4998    40143872    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a842d26

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         156     1253038+   7  HPFS/NTFS
/dev/sdb2             157       52970   424228455    7  HPFS/NTFS
/dev/sdb3           52971       60801    62902507+   5  Extended
/dev/sdb5           52971       60476    60291913+  83  Linux
/dev/sdb6           60477       60801     2610531   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a7278

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60802   488384017    7  HPFS/NTFS



windows 7 is on sdb2

here is my menu.lst entry for windows 7

title		Windows Vista (loader)
root	(hd1,2)
makeactive
chainloader	+1

---

### Post by Dfairlite on 2010-02-28
also, i have tried changing the root (hd1,2) to 1,0 1,1 and 0,1 0,2

---

### Post by presence1960 on 2010-02-28
I need two things: the order of hard disk booting in the hard disk boot order in BIOS and then to see your setup & boot process do the following.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by Chirola on 2010-03-05
I've windows 7 installed, but right now i can only boot into ubuntu.

(after a long time expended, and special thanks to a member of this forum, **meierfra** \\:D/ ,i could finally restore my linux partition,that was messed up when i've installed windows 7, install grub, and boot into ubuntu
topic: [http://ubuntuforums.org/showthread.php?t=1419274&page=5](http://ubuntuforums.org/showthread.php?t=1419274&page=5) ) .

But,when i try to boot windows, it appears to me a message in big red letters, "ERROR", and it also says in the top of the screen "cannot find c:\recovery.dat"

I've searched other forums and they said it's because of the recovery partition that i still have in my hdd.

My recovery partition is in sda1, has you can see in the image.

Can you give me a "sudo command" so i can delete this partition and finally boot windows?
Unless there is another way of booting windows without deleting the reovery partition, 
i am all hears;)

EDIT: if i delete recovery, sda2 remains windows,and sda5 remains linux?

---

### Post by whatdoesitwant on 2010-03-06
Hi, I have Windows 7 installed on a intel ich9r chip (gigabyte ds4) with 4 hdd's in raid 1+0. My system does not have an fdd. Should I attempt a karmic installation to dual boot or just forget about it. I am willing to put in a day of my time. I have done standalone intallations of ubuntu jaunty before (desktop and server).

---

### Post by Nybb on 2010-03-13
So, I have a fresh install of Karmic on my laptop, and am trying to set up a dual boot with Windows 7. I installed Windows on a partition, so my system now has the Ubuntu one, a swap partition, and the Windows one. 

I booted into the Live CD to fix the boot-up stuff, and found out that I am supposed to use Grub2 now (I've successfully set up a dual boot like this before but with an older version of Ubuntu and Grub). After poking around on the internet for help, I tried to do the steps outlined here under _[Recover Grub 2 via Live CD]("https://wiki.ubuntu.com/Grub2")_. It all seemed to go fine, and now when I start the machine I successfully get into the Grub boot menu and can load Ubuntu, but the Windows 7 partition is not listed. How do I get Grub 2 to see the Windows partition? Apparently the old menu.lst is gone, so I'm not sure what to do.

---

### Post by presence1960 on 2010-03-13
> **Nybb said:**
> So, I have a fresh install of Karmic on my laptop, and am trying to set up a dual boot with Windows 7. I installed Windows on a partition, so my system now has the Ubuntu one, a swap partition, and the Windows one. 

I booted into the Live CD to fix the boot-up stuff, and found out that I am supposed to use Grub2 now (I've successfully set up a dual boot like this before but with an older version of Ubuntu and Grub). After poking around on the internet for help, I tried to do the steps outlined here under _[Recover Grub 2 via Live CD]("https://wiki.ubuntu.com/Grub2")_. It all seemed to go fine, and now when I start the machine I successfully get into the Grub boot menu and can load Ubuntu, but the Windows 7 partition is not listed. How do I get Grub 2 to see the Windows partition? Apparently the old menu.lst is gone, so I'm not sure what to do.

Boot into ubuntu, open a terminal and run ```
sudo update-grub
```Watch the terminal window to see if it detects windows. If it does it will be in your GRUB menu when you reboot. If that does not work a lot more info about your setup is definitely needed to troubleshoot.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by Zorrothustra on 2010-03-14
I've been searching for hours through this and other topics since my (pre-installed) Windows 7 continues to kill my grub loader whenever I boot windows. 

At first I succesfully installed Ubuntustudio on a partition just using the Ubuntustudio Install DVD (install process created the partition). After I restarted in Windows, Grub got stuck mentioning something like:

'sk-read' not found

Never had any trouble with dual boot before, but that was XP. I understand there are quite some issues with Vista and W7. I managed to repair the Grub with the Ubuntustudio install DVD but when I had to reboot after a Windows 7 session, the same problem began all over.

I found one thread that has discribed exactly the same problem with Ubuntu here: [http://ubuntuforums.org/showthread.php?t=1312267](http://ubuntuforums.org/showthread.php?t=1312267) (also on a Dell Studio 15 btw).

Now what ? Should I just start from zero and install windows 7 first, making a partition through Windows and then reinstalling Ubuntu in that partition, as some have suggested in this thread ? Is that partitioning method a garantee that Windows won't rape the MBR again ? Or is there an easier option that avoids reinstalling everything ? [EDIT]: I finally decided it was getting far too technical for me. I followed the steps I described in [http://ubuntuforums.org/showthread.php?t=1312267](http://ubuntuforums.org/showthread.php?t=1312267) (#7). It works for me now !

Also, I'd like to have 3 main partitions on one disk: one for Windows 7, one for Ubuntu, one for data. Somehow the number of partitions multiplied after the install-DVD-guided Ubuntu or Windows reparations. 

As I read the details are important, my RESULT.txt from the Boot Info Script: 



                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /etc/lilo.conf 
                       /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8a2a92b9

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              80,325    30,800,324    30,720,000   7 HPFS/NTFS
/dev/sda3    *     30,800,325   226,112,824   195,312,500   7 HPFS/NTFS
/dev/sda4         226,114,875   976,768,064   750,653,190   5 Extended
/dev/sda5         226,114,938   953,457,749   727,342,812  83 Linux
/dev/sda6         958,695,003   976,768,064    18,073,062  82 Linux swap / Solaris
/dev/sda7         953,457,813   958,341,509     4,883,697  83 Linux
/dev/sda8         958,341,573   958,694,939       353,367  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        5ACAE7A9CAE77F9D                       ntfs       RECOVERY                      
/dev/sda3        0272EB8172EB7835                       ntfs       OS                            
/dev/sda5        60b91566-6589-48f4-af65-9216f2fb6714   ext4                                     
/dev/sda6        164e0443-abf2-431f-afc7-55da8569e843   swap                                     
/dev/sda7        95d843a1-1005-416a-b12f-a22d2c1afccd   ext4                                     
/dev/sda8        ab9b83d2-4ca9-4102-9219-3275b2ad75d1   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda5        /media/60b91566-6589-48f4-af65-9216f2fb6714 ext4       (rw,nosuid,nodev,uhelper=devkit)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 60b91566-6589-48f4-af65-9216f2fb6714
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-9-rt" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 60b91566-6589-48f4-af65-9216f2fb6714
	linux	/boot/vmlinuz-2.6.31-9-rt root=UUID=60b91566-6589-48f4-af65-9216f2fb6714 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-9-rt
}
menuentry "Ubuntu, Linux 2.6.31-9-rt (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 60b91566-6589-48f4-af65-9216f2fb6714
	linux	/boot/vmlinuz-2.6.31-9-rt root=UUID=60b91566-6589-48f4-af65-9216f2fb6714 ro single 
	initrd	/boot/initrd.img-2.6.31-9-rt
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 5acae7a9cae77f9d
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=60b91566-6589-48f4-af65-9216f2fb6714 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=164e0443-abf2-431f-afc7-55da8569e843 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 117.1GB: boot/grub/core.img
 120.0GB: boot/grub/grub.cfg
 121.9GB: boot/initrd.img-2.6.31-9-rt
 118.1GB: boot/vmlinuz-2.6.31-9-rt
 121.9GB: initrd.img
 118.1GB: vmlinuz

=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,7)
search --no-floppy --fs-uuid --set 95d843a1-1005-416a-b12f-a22d2c1afccd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-9-rt" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 95d843a1-1005-416a-b12f-a22d2c1afccd
	linux	/boot/vmlinuz-2.6.31-9-rt root=UUID=95d843a1-1005-416a-b12f-a22d2c1afccd ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-9-rt
}
menuentry "Ubuntu, Linux 2.6.31-9-rt (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 95d843a1-1005-416a-b12f-a22d2c1afccd
	linux	/boot/vmlinuz-2.6.31-9-rt root=UUID=95d843a1-1005-416a-b12f-a22d2c1afccd ro single 
	initrd	/boot/initrd.img-2.6.31-9-rt
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 5acae7a9cae77f9d
	chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-9-rt (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 60b91566-6589-48f4-af65-9216f2fb6714
	linux /boot/vmlinuz-2.6.31-9-rt root=UUID=60b91566-6589-48f4-af65-9216f2fb6714 ro quiet splash
	initrd /boot/initrd.img-2.6.31-9-rt
}
menuentry "Ubuntu, Linux 2.6.31-9-rt (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 60b91566-6589-48f4-af65-9216f2fb6714
	linux /boot/vmlinuz-2.6.31-9-rt root=UUID=60b91566-6589-48f4-af65-9216f2fb6714 ro single
	initrd /boot/initrd.img-2.6.31-9-rt
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=95d843a1-1005-416a-b12f-a22d2c1afccd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=ab9b83d2-4ca9-4102-9219-3275b2ad75d1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

============================= sda7/etc/lilo.conf: =============================

# /etc/lilo.conf - See: `lilo(8)' and `lilo.conf(5)',
# ---------------       `install-mbr(8)', `/usr/share/doc/lilo/',
#                       and `/usr/share/doc/mbr/'.

# +---------------------------------------------------------------+
# |                        !! Reminder !!                         |
# |                                                               |
# | Don't forget to run `lilo' after you make changes to this     |
# | conffile, `/boot/bootmess.txt' (if you have created it), or   |
# | install a new kernel.  The computer will most likely fail to  |
# | boot if a kernel-image post-install script or you don't       |
# | remember to run `lilo'.                                       |
# |                                                               |
# +---------------------------------------------------------------+

# Specifies the boot device.  This is where Lilo installs its boot
# block.  It can be either a partition, or the raw device, in which
# case it installs in the MBR, and will overwrite the current MBR.
#
boot=/dev/sda

# Specifies the device that should be mounted as root. (`/')
#
#root=/dev/sda7

# This option may be needed for some software RAID installs.
#
# raid-extra-boot=mbr-only

# Enable map compaction:
# Tries to merge read requests for adjacent sectors into a single
# read request. This drastically reduces load time and keeps the
# map smaller.  Using `compact' is especially recommended when
# booting from a floppy disk.  It is disabled here by default
# because it doesn't always work.
#
# compact

# Installs the specified file as the new boot sector
# You have the choice between: text, bmp, and menu
# Look in lilo.conf(5) manpage for details
#
#install=menu

# Specifies the location of the map file
#
map=/boot/map

# You can set a password here, and uncomment the `restricted' lines
# in the image definitions below to make it so that a password must
# be typed to boot anything but a default configuration.  If a
# command line is given, other than one specified by an `append'
# statement in `lilo.conf', the password will be required, but a
# standard default boot will not require one.
#
# This will, for instance, prevent anyone with access to the
# console from booting with something like `Linux init=/bin/sh',
# and thus becoming `root' without proper authorization.
#
# Note that if you really need this type of security, you will
# likely also want to use `install-mbr' to reconfigure the MBR
# program, as well as set up your BIOS to disallow booting from
# removable disk or CD-ROM, then put a password on getting into the
# BIOS configuration as well.  Please RTFM `install-mbr(8)'.
#
# password=tatercounter2000

# Specifies the number of deciseconds (0.1 seconds) LILO should
# wait before booting the first image.
#
delay=20

# You can put a customized boot message up if you like.  If you use
# `prompt', and this computer may need to reboot unattended, you
# must specify a `timeout', or it will sit there forever waiting
# for a keypress.  `single-key' goes with the `alias' lines in the
# `image' configurations below.  eg: You can press `1' to boot
# `Linux', `2' to boot `LinuxOLD', if you uncomment the `alias'.
#
# message=/boot/bootmess.txt
#	prompt
#	delay=100
#	timeout=100

# Specifies the VGA text mode at boot time. (normal, extended, ask, <mode>)
#
# vga=ask
# vga=9
#


# Kernel command line options that apply to all installed images go
# here.  See: The `boot-prompt-HOWTO' and `kernel-parameters.txt' in
# the Linux kernel `Documentation' directory.
#
# append=""
 
# If you used a serial console to install Ubuntu, this option should be
# enabled by default.
# serial=

#
# Boot up Linux by default.
#
default=Linux

image=/vmlinuz
	label=Linux
	read-only
#	restricted
#	alias=1
	append="root=/dev/sda7  "
	initrd=/initrd.img

image=/vmlinuz.old
	label=LinuxOLD
	read-only
	optional
#	restricted
#	alias=2
	append="root=/dev/sda7  "
	initrd=/initrd.img.old


# If you have another OS on this machine to boot, you can uncomment the
# following lines, changing the device name on the `other' line to
# where your other OS' partition is.
#
# other=/dev/hda4
#	label=HURD
#	restricted
#	alias=3
other=/dev/sda2
	label=Windows
#	restricted
#	alias=2

=================== sda7: Location of files loaded by Grub: ===================


 488.7GB: boot/grub/core.img
 488.7GB: boot/grub/grub.cfg
 488.7GB: boot/initrd.img-2.6.31-9-rt
 488.6GB: boot/vmlinuz-2.6.31-9-rt
 488.7GB: initrd.img
 488.6GB: vmlinuz

--------------------------------END of RESULT.txt-------------------------

Thanks for your suggestions !

Z

---

### Post by Nybb on 2010-03-16
> **presence1960 said:**
> Boot into ubuntu, open a terminal and run ```
sudo update-grub
```Watch the terminal window to see if it detects windows. If it does it will be in your GRUB menu when you reboot. If that does not work a lot more info about your setup is definitely needed to troubleshoot.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

Thanks for the response! I tried running update-grub during my original attempts to get this to work, and I got
```

ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.
```

So, here are the results from your lovely script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006309c

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   265,715,099   265,715,037  83 Linux
/dev/sda2         265,715,100   281,346,344    15,631,245   5 Extended
/dev/sda5         265,715,163   281,346,344    15,631,182  82 Linux swap / Solaris
/dev/sda3    *    281,348,096   488,394,751   207,046,656   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        e0603a8c-3fc7-40b6-8238-17ed343fbd59   ext4                                     
/dev/sda3        CC36D2C636D2B0A6                       ntfs                                     
/dev/sda5        505db507-ec30-457f-8f70-3a14babd773e   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sda1/boot/grub/menu.lst: ===========================

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
timeout		7

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
# kopt=root=UUID=e0603a8c-3fc7-40b6-8238-17ed343fbd59 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e0603a8c-3fc7-40b6-8238-17ed343fbd59

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

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		e0603a8c-3fc7-40b6-8238-17ed343fbd59
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=e0603a8c-3fc7-40b6-8238-17ed343fbd59 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		e0603a8c-3fc7-40b6-8238-17ed343fbd59
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=e0603a8c-3fc7-40b6-8238-17ed343fbd59 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		e0603a8c-3fc7-40b6-8238-17ed343fbd59
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=e0603a8c-3fc7-40b6-8238-17ed343fbd59 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		e0603a8c-3fc7-40b6-8238-17ed343fbd59
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=e0603a8c-3fc7-40b6-8238-17ed343fbd59 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Chainload into GRUB 2
root		e0603a8c-3fc7-40b6-8238-17ed343fbd59
kernel		/boot/grub/core.img

title		Ubuntu 9.10, memtest86+
uuid		e0603a8c-3fc7-40b6-8238-17ed343fbd59
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set e0603a8c-3fc7-40b6-8238-17ed343fbd59
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e0603a8c-3fc7-40b6-8238-17ed343fbd59
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=e0603a8c-3fc7-40b6-8238-17ed343fbd59 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e0603a8c-3fc7-40b6-8238-17ed343fbd59
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=e0603a8c-3fc7-40b6-8238-17ed343fbd59 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e0603a8c-3fc7-40b6-8238-17ed343fbd59
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e0603a8c-3fc7-40b6-8238-17ed343fbd59 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e0603a8c-3fc7-40b6-8238-17ed343fbd59
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e0603a8c-3fc7-40b6-8238-17ed343fbd59 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=e0603a8c-3fc7-40b6-8238-17ed343fbd59 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=505db507-ec30-457f-8f70-3a14babd773e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .9GB: boot/grub/core.img
  17.3GB: boot/grub/grub.cfg
   5.6GB: boot/grub/menu.lst
    .1GB: boot/grub/stage2
    .5GB: boot/initrd.img-2.6.31-14-generic
    .7GB: boot/initrd.img-2.6.31-20-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .6GB: boot/vmlinuz-2.6.31-20-generic
    .7GB: initrd.img
    .5GB: initrd.img.old
    .6GB: vmlinuz
    .5GB: vmlinuz.old
```

---

### Post by silntdoogood on 2010-03-16
This is throwing errors at me left and right. I probably already royally screwed this up, but windows is still there, so I haven't given up hope. I had 7 installed, then ubuntu, it ate the option to boot 7(as described) after install. 

The first time I went through, I tried it, it said "GRUB" is not installed, and gave me the command to install it, I entered it, it said it would replace GRUB-PC, so now I get to the better part of step 4. On "grub> find /boot/grub/stage1" I get the response "Error 15: file not found" 

I tried skipping ahead to the "sudo gedit /boot/grub/menu.lst" and it just opens a blank doc, rather than a long list as described.

---

### Post by presence1960 on 2010-03-16
> **silntdoogood said:**
> This is throwing errors at me left and right. I probably already royally screwed this up, but windows is still there, so I haven't given up hope. I had 7 installed, then ubuntu, it ate the option to boot 7(as described) after install. 

The first time I went through, I tried it, it said "GRUB" is not installed, and gave me the command to install it, I entered it, it said it would replace GRUB-PC, so now I get to the better part of step 4. On "grub> find /boot/grub/stage1" I get the response "Error 15: file not found" 

I tried skipping ahead to the "sudo gedit /boot/grub/menu.lst" and it just opens a blank doc, rather than a long list as described.

I need to see your setup & boot process first. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by davoudi on 2010-03-17
This article [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) discuss two different methods of creating dual boots (windows&ubuntu). Windows is installed prior to ubuntu in the first method which makes this method very attractive since most people doesn't have windows's CD. Ubuntu is installed after windwss and GRUB take care of booting. Has anybody ever try this? Let me know and I will give it a try.

---

### Post by fazlee on 2010-03-18
im having a similar problem.. i just recently installed ubuntu os to my system which i already had windows 7..  so i shrink my hard drive into 300 gb each.. now i can't  seem to boot windows 7 only.. i can only access to ubuntu and my recovery driver which it came with computer but not windows 7...  i can access all the windows file thro ubuntu..win 7 is on c drive... how come it doesn't show up in the boot... i did everything...

here is my info.... please help me to completely restore to windows 7...


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 62709260 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #3 for /boot/grub. No errors found 
                       in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcfa050e1

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    31,459,327    31,457,280  27 Hidden HPFS/NTFS
/dev/sda2    *     31,459,328    31,664,127       204,800   7 HPFS/NTFS
/dev/sda3          31,680,180   748,404,089   716,723,910  83 Linux
/dev/sda4         748,404,090 1,465,145,343   716,741,254   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D81ADEFB1ADED61A                       ntfs       PQSERVICE                     
/dev/sda2        E2E0DFABE0DF83E7                       ntfs       SYSTEM RESERVED               
/dev/sda3        9e6adc36-ab1c-488d-921c-0aa5fbd685ca   ext4                                     
/dev/sda4        44AEE0E8AEE0D388                       ntfs       Acer                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sda4        /media/Acer              fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set 9e6adc36-ab1c-488d-921c-0aa5fbd685ca
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 9e6adc36-ab1c-488d-921c-0aa5fbd685ca
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=9e6adc36-ab1c-488d-921c-0aa5fbd685ca ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 9e6adc36-ab1c-488d-921c-0aa5fbd685ca
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=9e6adc36-ab1c-488d-921c-0aa5fbd685ca ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set d81adefb1aded61a
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set e2e0dfabe0df83e7
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=9e6adc36-ab1c-488d-921c-0aa5fbd685ca /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  16.7GB: boot/grub/core.img
  17.0GB: boot/grub/grub.cfg
  16.8GB: boot/initrd.img-2.6.31-14-generic
  16.7GB: boot/vmlinuz-2.6.31-14-generic
  16.8GB: initrd.img
  16.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdf

---

### Post by presence1960 on 2010-03-18
> **fazlee said:**
> im having a similar problem.. i just recently installed ubuntu os to my system which i already had windows 7..  so i shrink my hard drive into 300 gb each.. now i can't  seem to boot windows 7 only.. i can only access to ubuntu and my recovery driver which it came with computer but not windows 7...  i can access all the windows file thro ubuntu..win 7 is on c drive... how come it doesn't show up in the boot... i did everything...

here is my info.... please help me to completely restore to windows 7...


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 62709260 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #3 for /boot/grub. No errors found 
                       in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcfa050e1

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    31,459,327    31,457,280  27 Hidden HPFS/NTFS
/dev/sda2    *     31,459,328    31,664,127       204,800   7 HPFS/NTFS
/dev/sda3          31,680,180   748,404,089   716,723,910  83 Linux
/dev/sda4         748,404,090 1,465,145,343   716,741,254   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D81ADEFB1ADED61A                       ntfs       PQSERVICE                     
/dev/sda2        E2E0DFABE0DF83E7                       ntfs       SYSTEM RESERVED               
/dev/sda3        9e6adc36-ab1c-488d-921c-0aa5fbd685ca   ext4                                     
/dev/sda4        44AEE0E8AEE0D388                       ntfs       Acer                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sda4        /media/Acer              fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set 9e6adc36-ab1c-488d-921c-0aa5fbd685ca
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 9e6adc36-ab1c-488d-921c-0aa5fbd685ca
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=9e6adc36-ab1c-488d-921c-0aa5fbd685ca ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 9e6adc36-ab1c-488d-921c-0aa5fbd685ca
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=9e6adc36-ab1c-488d-921c-0aa5fbd685ca ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set d81adefb1aded61a
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set e2e0dfabe0df83e7
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=9e6adc36-ab1c-488d-921c-0aa5fbd685ca /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  16.7GB: boot/grub/core.img
  17.0GB: boot/grub/grub.cfg
  16.8GB: boot/initrd.img-2.6.31-14-generic
  16.7GB: boot/vmlinuz-2.6.31-14-generic
  16.8GB: initrd.img
  16.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdf

Hopefully you shrank Windows 7 with it's own disk management utility. If you did not and used another partitioning tool this is most likely why you can not boot windows. The fix is easy but will involve fixing windows boot & then reinstalling GRUB 2. You will need a windows 7 install DVD. If you don't have one you can get a recovery console only CD [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/"). Download the iso and burn it as an image to CD. Then follow the instructions for windows 7 [here]("http://ubuntuforums.org/showthread.php?t=1014708"). When complete reboot without the CD and make sure windows boots properly. If it does you will now need to boot from your 9.10 ubuntu Live CD to restore GRUB.

Boot from the Live CD and choose "try ubuntu without any changes." When the desktop loads open a terminal and run ```
sudo mount /dev/sda3 /mnt
```This will mount your ubuntu / partition. Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```When complete reboot without the Live CD and try booting windows from GRUB

---

### Post by fazlee on 2010-03-18
ok when i try to load windows 7 cd.. its saying it can't install coz of different file system..  so i think i need to format again and install back windows... but im having touble installing.. any help i have all the cds.... sorri im new to this.. thanks alot for ur kind help...

---

### Post by presence1960 on 2010-03-18
> **fazlee said:**
> ok when i try to load windows 7 cd.. its saying it can't install coz of different file system..  so i think i need to format again and install back windows... but im having touble installing.. any help i have all the cds.... sorri im new to this.. thanks alot for ur kind help...

You must be doing something wrong, you should not be at a window or screen where the install takes place. Here are the instructions:

[B][COLOR="Red"]1. To restore the Windows Vista/7 bootloader, you must first boot off your Windows Vista/7 installation DVD.

2. When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer."

3. On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the following:

```
bootrec.exe /fixboot
```

```
bootrec.exe /fixmbr
```

Now close the two windows and click "Restart."[/COLOR][/B]

---

### Post by fazlee on 2010-03-18
i must have done something wrong i can't even install my windows 7 from the cd.. i get this error from grub booter...  ok this is wat i did.. so i used live cd to boot with out installing ubuntu.. i went to that format tool... i deleted both my ubuntu and windows 7 drive.. made it to one hole new drive formated to ntfs.. then i used my windows 7 cd to install .. mm it installed fine.. but after the rester i still get grub error.. it goes something rescue dos command thing.. any help thanks...

---

### Post by presence1960 on 2010-03-18
> **fazlee said:**
> i must have done something wrong i can't even install my windows 7 from the cd.. i get this error from grub booter...  ok this is wat i did.. so i used live cd to boot with out installing ubuntu.. i went to that format tool... i deleted both my ubuntu and windows 7 drive.. made it to one hole new drive formated to ntfs.. then i used my windows 7 cd to install .. mm it installed fine.. but after the rester i still get grub error.. it goes something rescue dos command thing.. any help thanks...

You really have trouble following directions, you did not have to format the entire disk & reinstall. Now try it one more time to fix the MBR so windows will boot: Go back to post # 207 and follow those directions.

Make sure you download the win 7 Recovery CD from [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/") and use that!

---

### Post by fazlee on 2010-03-18
the cd i have is acer system recovery cd.. it install fine.. but i dont see any repair ur computer.. i didn't sleep like hole day... trying to fix this... any other method?

---

### Post by fazlee on 2010-03-18
thanks alot presence1960 for all ur help.. ok i really tired of this lol.. im just gonna install ubuntu on my 700 gb hard drive first.. and see how it goes.. then maybe i can resize/move to make new partition and install windows 7 is that possible? i like ubuntu..
 
ok i got it to work... i just installed windows 7 and i used that system recovery disk..  i reset the boot loader...  all i did was on dos comman "bootrec.exe /fixboot" and this command 'bootrec.exe /fixmbr"  this is for vista/7 only...  now i will make a new partition using windows built in parition manager.. and install ubuntu back hopefully everything will work fine.. wish me luck lol

---

### Post by infinitybrain on 2010-03-19
> **marmel said:**
> Hi hyperdude111,

Thanks for the guide! Unfortunately it didn't work for me... :( When I boot Windows 7 via grub the system resets after trying to load Windows and no error message is displayed. I am sure that the partition number in the grub entry is correct (sda1 -> hd0,0).

Any suggestion?

Thank you so much!
[http://www.mediafire.com/?sharekey=ffa962b03f06ebdd7069484bded33bcd54946d876c3b5458](http://www.mediafire.com/?sharekey=ffa962b03f06ebdd7069484bded33bcd54946d876c3b5458)

---

### Post by Asham on 2010-03-19
Sorry that I didn't take the time to search first but...

regarding sections 4 and 5: wouldn't a clever shell script be able to automate these steps? 

I don't trust my own eyes and finger tips when it comes to this kind of crucial stuff! :P

---

### Post by Nybb on 2010-03-20
presence1960, you have been quite active in this thread (I'm sure everyone is very grateful). You responded to my original query but it looks like you missed my reply with the results of running your script; it was hiding at _[the bottom of a page]("http://ubuntuforums.org/showpost.php?p=8974891&postcount=200")_. Thanks again for being so willing to help!

---

### Post by dert on 2010-03-24
> **chessplayer said:**
> This is in reply to the very first post in this thread by hyperdude111 and following the link provided by presence1960:

Hyperdude111 wrote the following "algorithm":

1.	Obtain a copy of Windows7.
2.	Partition your disk with gparted.
3.	Install Windows7.
4.	Re-install Grub.
5.	Edit Grub to List Windows 7.
6.	Have Fun.

The point is that points 4 and 5 can now (i.e. with 9.10 (karmic)) be done automatically, if you have a live CD or USB-Stick!

Step 4 becomes booting from live device and following [http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD")

Step 5 then just needs booting the installed ubuntu and doing what [http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-mkconfig]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#grub-mkconfig")  has to say

The "Have fun" part stays the same!

Hi guys.  This is my FIRST ever dual boot system.  I have to tell all you guys that are struggling with the multiple sets of instructions you're trying, you HAVE to be doing something wrong or not following directions at all.  I performed the following and it went flawlessly.  My method is IDENTICAL to the instructions provided above and you REALLY need to follow them EXACTLY!!

1.  I downloaded Ubuntu Studio 9.10 x64 and installed it.  No problem.
2.  I Partitioned my drive with gparted leaving Ubuntu first and the new NTFS Windows 7 partition second.  I even labelled them with the new Label function in gparted!
3.  I installed Windows 7, selecting the new, 2nd partition.  It went flawlessly.
4.  I performed the NEW Step 4 instructions provided above TO THE LETTER using the Ubuntu 9.10 DESKTOP LIVE CD (there is no Ubuntu Studio Live CD but it's not necessary) and re-installed Grub.  No problems.
5.  I performed the NEW Step 5, running grub-mkconfig, which AUTOMATICALLY updates grub to include Windows 7!
6.  I'm having fun!  It boots to a selection screen where you can select Ubuntu, Windows 7, Mem Tests and other stuff.

A flawless, issue free dual boot Ubuntu/Windows 7!  I'm not a rocket scientist, can't do anything in Linux without googling it first and it was EASY peasy to do this.  I even did this on the new 4096 byte sector drives!  The "advanced format" drives from Western Digitial.  So far, write times are excellent and all is well.

STOP TRYING SO HARD and making this way overcomplicated.  If you follow my steps above, you cannot fail.  I didn't and I'm stoopid!  #-o

---

### Post by MontBlue on 2010-04-14
When I go to insert the win 7 disk my computer won't recognize it. I've put the disk on other computers to make sure it wasn't faulty and I know it works. My drive recognizes other disks. It will show that there is a disk in the drive but that is all it will do. Are there drivers that I need to download? Any suggestions?

---

### Post by xdevnull on 2010-04-20
Okay - here's a quick question.  I'm currently running Karmic (and that's it). I'm planning on installing Lucid (probably once RC is released, because then running an update, not much changes).

I always do a clean install in a / partition, while /home is a separate partition with all my stuff (which I then move over to the new user folder)...

Anyway, so I have 3 partitions other than swap -- a 8 gig ext3 for / ; a 185 gig ext3 partition for /home ; and a 38 gig NTFS partition for windows 7 with nothing on it.

So can I install windows 7 on the 38 gig partition - then do a clean install of lucid - and since grub installs at that point, have a system that easily boots to either OS?

I would just need to wait a couple of days to save myself from hacking around in grub...

Thanks,

---

### Post by kyklops on 2010-05-09
I would summarize the "algorithm". You have Ubuntu 9.10 or following version (because of GRUB2) already installed.

[LIST=1]
[*]Obtain a copy of Windows 7

[*]Partition your disk with Gparted. Is not important if the NTSF partition is before or after the Ubuntu partition. The important thing is that YOU create the NTFS partition where Windows will be installed, and not the Windows 7 installation process. In fact it creates a small partition of 100MB also (something like that [http://cache.gawker.com/assets/images/lifehacker/2009/11/gparted.jpg](http://cache.gawker.com/assets/images/lifehacker/2009/11/gparted.jpg)). That produce some problems in Grub2.

[*] Install Windows 7 in the previous created partition.

[*] Boot from an Ubuntu 9.10 (or following) live CD and from terminal type:
```
sudo grub-setup -d /media/disk/boot/grub /dev/sda
```
where *disk* is the partition where ubuntu is installed and */dev/sda* refers to the MBR to overwrite in order to boot from ubuntu on the next reboot.

[*] Restart and from terminal type:
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
``` in order to list Windows 7 in the Grub menu on startup.
[/LIST]

---

### Post by fawkesey on 2010-05-23
Thanks [kyklops]("http://ubuntuforums.org/member.php?u=697001"), those steps worked for me on Lucid too.

---

### Post by darktachyon on 2010-05-29
Cheers, OP.

Worked with Ubuntu 10.04 running legacy grub.

Nice smooth install.

---

### Post by GutsyVirgin on 2010-06-11
Oh dear me... the 8Gb recommendation is by no means adequate. I'd recommend at least 20Gb for 32-bit and 25Gb for 64-bit. If you plan on installing any Adobe software (which forces you to install at least a large portion of the software on your C drive), then it would be a good idea to add another 3-5Gb extra to accommodate the swap, etc. Good luck! :)

---

### Post by lazyrobot47 on 2010-06-28
I'm so confused trying to figure this out. I want gParted to set aside about 150 gigs for windows 7 and leave the rest to Ubuntu, but I don't want to lose all data by repartitioning my hard drive, is there any way around that? I don't want to lose how I have Ubuntu set up on here, I want to be able to install Win 7 without affecting my Ubuntu installation at all. 

Halp? :lolflag:

---

### Post by wilee-nilee on 2010-06-28
> **lazyrobot47 said:**
> I'm so confused trying to figure this out. I want gParted to set aside about 150 gigs for windows 7 and leave the rest to Ubuntu, but I don't want to lose all data by repartitioning my hard drive, is there any way around that? I don't want to lose how I have Ubuntu set up on here, I want to be able to install Win 7 without affecting my Ubuntu installation at all. 

Halp? :lolflag:

First whenever repartitioning you should have the stuff you don't want to lose backed up, chances are nothing will happen but if it gets corrupted you could lose stuff. Take a screenshot of gparted and post it.

---

### Post by Mr Coffee on 2010-07-13
Hmm... Having problems partitioning through gparted. Was unsure whether to create a new topic or not. This is the screen i get;
[IMG]http://i31.tinypic.com/ebekyd.png[/IMG]

Can't format, resize or do anything. There's also another FAT32 external hard drive, but it's the same deal, won't do anything.

---

### Post by 99digit on 2011-01-13
Will this also work with Ubuntu 10.04 LTS? or even the Page 15 tut?

Which one should i follow? installing win xp though.

---

### Post by dirtcrusher on 2011-03-06
> **Mr Coffee said:**
> Hmm... Having problems partitioning through gparted. Was unsure whether to create a new topic or not. This is the screen i get;
[IMG]http://i31.tinypic.com/ebekyd.png[/IMG]

Can't format, resize or do anything. There's also another FAT32 external hard drive, but it's the same deal, won't do anything.

That's because the partition is mounted. Try to do it from a Live-CD, it should work.

---

### Post by Derringer81 on 2011-05-15
So i tried this and it looks like ubuntu 11 is different?

i did:
$sudo gedit /boot/grub/menu.lst 
and the gedit page was empty. I tried to go to that location and the file is not even there.....

so how do i back this up so when i install windows i can get it to dual boot properly??

I am wanting to install windows on a totally separate drive, so in theory, both OSs are bootable (i am a n00b so im not totally sure) can i hook windows into grub or Ubuntu into the windows boot manager ?

(if this was brought up earlier i am sorry, i didn't comb the whole thing)

---

### Post by easybake on 2011-05-18
> **Derringer81 said:**
> So i tried this and it looks like ubuntu 11 is different?

i did:
$sudo gedit /boot/grub/menu.lst 
and the gedit page was empty. I tried to go to that location and the file is not even there.....

so how do i back this up so when i install windows i can get it to dual boot properly??

I am wanting to install windows on a totally separate drive, so in theory, both OSs are bootable (i am a n00b so im not totally sure) can i hook windows into grub or Ubuntu into the windows boot manager ?

(if this was brought up earlier i am sorry, i didn't comb the whole thing)

It's cool, Grub has been updated to Grub2 you can read about it here: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by buntu2020 on 2011-05-18
I have Win 7 installed can install ubuntu with it or do i have to uninstall my Win 7 before installing ubuntu?



> **hyperdude111 said:**
> “How to” Dual boot Ubuntu and Windows 7 (Ubuntu installed first)

##This guide does not work for Karamic or future releases, For that see page 14 and follow the link provided by presence1960 for how to dual boot with Grub2 (requires some reading) I will update this guide for grub2 when I have more time## 

I have recently seen many posts from people trying to dual boot Ubuntu and Windows 7 beta, but not succeeding. So I tried it out myself and found a solution.
Index
1.    Obtain a copy of Windows7.
2.    Partition your disk with gparted.
3.    Install Windows7.
4.    Re-install Grub.
5.    Edit Grub to List Windows 7.
6.    Have Fun.
__________________________________________________________________________________

1.    Obtain a copy of windows 7.  

*You can also find a torrent of this but for legal reasons I cannot provide a link. *


2.    Partition your disk 

**This does go wrong in some cases, if in doubt back up your valuable data.**

Boot from a Ubuntu live cd or a gparted live cd.
Start up gparted, If ubuntu is on the whole disk you need to re-size it by at least 8 gb for Windows 7. (Make sure windows 7 is on the second partition to make it easier for grub) You will be left with some unallocated space on your hard disk if you want you can partition it to NTFS or you can do it later on the windows install.

3.    Install Windows 7

Follow the on screen instructions, Select the un-partitioned space to format and install windows on, or if you already made it NTFS choose your NTFS partition. 

**It will ask for a product key but you have 30 days to do that. Note: Beta keys will work with the RC**

  
4.    Re-install GRUB

Now you have windows 7 but it has completely eaten your boot loader so you need to re-install grub. 
Boot from the ubuntu live cd and go to terminal.
Type in terminal:

"sudo grub"
"grub> find /boot/grub/stage1"

That should return your Ubuntu partition in the form of (hdX,Y), use that:

grub> root (hdX,Y)
grub> setup (hd0)
grub> quit

(you don’t need to type the grub> bit)

That has re-installed grub but you can no longer see windows7

5.    Edit grub.
Go to terminal from normal ubuntu and type :

“sudo gedit /boot/grub/menu.lst”

A large text file will open and at the bottom leave a line and add this:

title        windows 7 beta (Loader)
root        (hd0,1)
savedefault
makeactive
chainloader    +1

(Do not type this line but if that does not work on re-boot try “hdo,0 or hd0,2” and so on until it works.)

 Now that is done you can re-boot  into windows 7 and ubuntu happily :)

******************Edit***********************
Hi
I have remembered that if you also have vista installed on your machine when you in install 7, that windows 7 will add itself to the vista bootloader.

So You will need to point grub to the vista partition so it will load the vista loader and give you the option for 7 and vista. 

Also To work out what partition number your 7 partiton is use gparted it will give you results like "Windows 7 sda2" that means hda0,2 or if you have two internal hard drives than change the tab in  the top right to the appropriate disk. Then take note of the sda2 but as it is on the 2nd drive it will be hda1,2. And so on.......... 
****************Edit*************************
Wow over 20,000 views

---

### Post by joelseff on 2011-05-21
Uhh Why dont you guys just choose the "Install Ubuntu Side by Side with Windows 7"?????
Worked like a charm for me and no rigmarole with the grub2.....

You just have to install win 7 FIRST!!!

---

### Post by Tornikee on 2011-06-07
I have a bit of noobish question: I successfully changed partitions to create a new NTFS partition for installing Windows 7, but my system doesn't offer me to boot from Windows installation CD after restart - it heads straight to Ubuntu login screen. How can I enter Windows installation?

Thanks in advance.

---

### Post by Tornikee on 2011-06-08
P.S. This is how my partitions look like:

[IMG]http://i.imgur.com/0uwLN.png[/IMG]

---

### Post by Tornikee on 2011-06-08
NVM, the problem was the Windows 7 installation DVD which couldn't be recognized. I first installed Windows XP and then replaced it with Windows 7.

---

### Post by Tornikee on 2011-11-22
Is it definite that this method won't work for current versions (as mentioned in the first post)? Would like to install Windows 7 64-bit beside Ubuntu 11.10. Currently have Windows 7 32-bit, so just want to replace it.

---

### Post by presence1960 on 2011-11-22
> **Tornikee said:**
> Is it definite that this method won't work for current versions (as mentioned in the first post)? Would like to install Windows 7 64-bit beside Ubuntu 11.10. Currently have Windows 7 32-bit, so just want to replace it.

This method won't work for current versions of Ubuntu because the method described in the first post is for versions of Ubuntu using legacy GRUB.

You can still install Ubuntu first, then add Windows 7. As before you will need to reset GRUB 2 as the boot loader on MBR. You can do so by following [these instructions]("https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2")

The above instructions are part of a larger guide to GRUB 2: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Tornikee on 2011-11-23
Thanks a lot.

---

