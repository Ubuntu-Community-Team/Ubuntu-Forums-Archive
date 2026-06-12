---
title: "Kernel Panic booting zenwalk"
date: 2007-03-12
forum: Slackware and derivatives
---

### Post by Captain_Riker on 2007-03-12
Hello there,

I've been searching forums now for a couple of days, and the closest thread to my problem was this:

[http://ubuntuforums.org/showthread.php?t=236932&highlight=kernel+panic+zenwalk](http://ubuntuforums.org/showthread.php?t=236932&highlight=kernel+panic+zenwalk)

Hope the link works . . .

Anyway it didn't solve my problem, wich is slightliy different.

I installed zenwalk on the the same HDD on wich I run my Ubuntu. It is contained in but one single partition and no bootloader whatsoever was installed. I just added the recommended and logicaly neccessary lines to my menu.lst of grub.
After booting I get the same error as many others who installed their zenwalk on external usb drives. For reasons I haven't understood yet completley they needed to create a new intrd.img! BTW I installed from the standard zenwalk CD, not from the LiveCD.

Next is a quote from my menu.lst:

[I]title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,4)
kernel          /vmlinuz-2.6.17-11-generic root=/dev/hda11 ro quiet splash
initrd          /initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,4)
kernel          /vmlinuz-2.6.17-11-generic root=/dev/hda11 ro single
initrd          /initrd.img-2.6.17-11-generic
boot

title           Zenwalk 4.4.1
root            (hd0,9)
kernel          /boot/vmlinuz-2.6.20             root=/dev/hda10 quiet splash
initrd          /boot/initrd.splash
boot
[/I]

Here fstab:

[I]# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/hda11
UUID=00f5e7ee-68e4-47b7-a017-e9dadadf613c /               ext3    defaults,errors=remount-ro 0       1

# /dev/hda5
UUID=635f81c2-f34e-43d4-8c6b-37b8280972d2 /boot           ext3    defaults        0       2

# /dev/hda1
UUID=459D-0443  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/hda7
UUID=AA5E29944293DDC1 /win_data       ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

# /dev/hda6
UUID=F2A8902EA88FEF81 /win_****       ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

# /dev/hda8
UUID=01F827948847F290 /win_swap       ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

# /dev/hda12
UUID=409e3812-55c5-4abe-9c6f-501c2716e9d3 /zdat           ext3    defaults        0       2

# /dev/hda10
UUID=8bfe8d3d-8a6d-44c9-8f5d-7d24341bdcf0 /zenwalk        ext3    defaults        0       2

# /dev/hda9
UUID=c6045c15-8fef-4a1a-adde-acced9412a98 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
:
[/I]

As you can see the entry in my menu.lst must be correcct for grub starts counting from 0 while the rest starts from 1.

The result is the known:

[I]Kernel Panic - not sysncing: VFS: unable to mount rootfs on unknown-block(0,0)
[/I]
The weired thing about me is, that before you start giving answers and help solve my problem, I want to understand whats wrong. Nevertheless. I really appreciate any help and look forward to it, for the community is the most powerfull advance Linux user have in compare to other OS users. They have theier own, but there is not half as much knowlegde and wisdom in it than here . . . 

Sorry drifted into a sermon, don't wont to bore you, just a follower praising . . .

However any suggestion what it is? And how to solve it?

Thanks in advance

---

### Post by RAV TUX on 2007-03-12
moving to the **[[B]Slackware**]("http://www.ubuntuforums.org/forumdisplay.php?f=163") **and derivatives forum**
[/B]

---

### Post by Captain_Riker on 2007-03-14
I'm a laughing OUT LOUD!!!!!!!

Really folks, this is something . . . . . 

I was, like I said, reading hundreds of pages of Threads about the same problem. Here comes the SOLUTION I figured out myself. BTW: If you can read, you are really in advance!! (I mean myself!!!!!)

So I was about to try and install Zenwalk 4.4.1 on a very old Laptop (lets say from 1997) because the Ubuntu-LiveCD failed booting and I was just keen to see what will happen. I know, there is still Xubuntu . . .

At first I didn't see it. But as I had to try it several times, I took the time reading what it says at the first  prompt. Where you can pass other options to the Kernel before booting the installer.

After the Welcome line it says:

***The Kernel is configured with exclusive LIBATA subsystem, all SATA and PATA devices are now called "sdX" (_no more "hdX" for PATA)_. Optical devices are called "srX".***

So simply changing the entry in the menu.lst from:
[I]
title Zenwalk 4.4.1
root (hd0,9)
--> kernel /boot/vmlinuz-2.6.20 root=**/dev/hda10** quiet splash !!!!!
initrd /boot/initrd.splash
boot[/I]

to:
[I]
title Zenwalk 4.4.1
root (hd0,9)
--> kernel /boot/vmlinuz-2.6.20 root=**/dev/sda10** quiet splash !!!!!
initrd /boot/initrd.splash
boot[/I]

fixes it. (Before you judge too quick, I don't HAVE an SATA HDD!!!!! It's PATA. Plain old simple IDE!!!)

Got it?? :lolflag: 

I marked it. It's just one letter, change an h to an s. That's it. So I'll keep on laughing for a while . . . 

:guitar:

---

### Post by tommcd on 2007-03-19
> **Captain_Riker said:**
> I'm a laughing OUT LOUD!!!!!!!

Really folks, this is something . . . . . 

I was, like I said, reading hundreds of pages of Threads about the same problem. Here comes the SOLUTION I figured out myself. BTW: If you can read, you are really in advance!! (I mean myself!!!!!)

So I was about to try and install Zenwalk 4.4.1 on a very old Laptop (lets say from 1997) because the Ubuntu-LiveCD failed booting and I was just keen to see what will happen. I know, there is still Xubuntu . . .

At first I didn't see it. But as I had to try it several times, I took the time reading what it says at the first  prompt. Where you can pass other options to the Kernel before booting the installer.

After the Welcome line it says:

***The Kernel is configured with exclusive LIBATA subsystem, all SATA and PATA devices are now called "sdX" (_no more "hdX" for PATA)_. Optical devices are called "srX".***

So simply changing the entry in the menu.lst from:
[I]
title Zenwalk 4.4.1
root (hd0,9)
--> kernel /boot/vmlinuz-2.6.20 root=**/dev/hda10** quiet splash !!!!!
initrd /boot/initrd.splash
boot[/I]

to:
[I]
title Zenwalk 4.4.1
root (hd0,9)
--> kernel /boot/vmlinuz-2.6.20 root=**/dev/sda10** quiet splash !!!!!
initrd /boot/initrd.splash
boot[/I]

fixes it. (Before you judge too quick, I don't HAVE an SATA HDD!!!!! It's PATA. Plain old simple IDE!!!)

Got it?? :lolflag: 

I marked it. It's just one letter, change an h to an s. That's it. So I'll keep on laughing for a while . . . 

:guitar:

In case you are interested, here is my grub entry for zenwalk. I triple boot windows, ubuntu, and zenwalk 4.4.1, which was upgraded from zen 4.2:
------------------------------------------------------------------------
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Zenwalk Linux (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz root=/dev/sda5 
initrd		/boot/initrd.splash
savedefault
boot
--------------------------------------------------------------------------
This was automagically added after I had to reinstall ubuntu (I mistakenly allowed zen to reformat my ubuntu partition). Notice there is no kernel number. Just /boot/vmlinuz root=/dev/sda5 . After I upgraded from zen 4.2 to zen 4.4.1 I did not have to update grub at all. Zenwalk does not save old kernels though.

---

### Post by hanzomon4 on 2007-07-16
I'm getting a kernel panic as well, Zenwalk is installed on my usb hard drive and the grub line looks correct. I've tried everything but nothing works. Here's the the grub line```
title Zenwalk
root (hd1,0)
kernel /boot/vmlinuz root=/dev/sdb
``` 

And the output of fdisk -l```
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1912    15358108+  83  Linux
/dev/sdb2            1913        3910    16048935   83  Linux
/dev/sdb4           12005       12188     1477948+  82  Linux swap / Solar
```

Any ideas how to fix this? I really want to try out a slack based distro..

---

