---
title: "Error 13: Invalid or unsupported executable format"
date: 2010-08-02
forum: Server Platforms
---

### Post by Shadowfire on 2010-08-02
Some information before I go in to the problem.

System:
------ 
AMD Quad-core
8GB Mem
1 RAID - (2) 320 WD HDD
Ubuntu 9.04 Server (64bit)

For some reason the power went out and my UPS is not working like it should, so the server turned off.  Unfortunately when I turned it on a day or so later after finding it off, it came up with the -

Error 13: Invalid or unsupported executable format

I went searching on the Internet about this error and found a number of references like - 

[http://www.webdeveloper.com/forum/showthread.php?t=174383](http://www.webdeveloper.com/forum/showthread.php?t=174383) (but my system is only Ubuntu and not dual booting.)

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/365331](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/365331) (should work sez others in the thread - but it doesn't I get the following)

When I try to setup /dev/sda1 through /mnt/linux  by the following..

boot from the live medium and chroot into the Linux installation:

--

$ sudo mkdir /mnt/linux
$ sudo mount -t ext4 /dev/sda1 /mnt/linux
$ sudo mount -t proc proc /mnt/linux/proc
$ sudo mount -t sysfs sys /mnt/linux/sys
$ sudo mount -o bind /dev /mnt/linux/dev
$ sudo chroot /mnt/linux

If /boot is on a separate partition, this partition must also be mounted:

$ sudo mount -t ext4 /dev/sdaX /boot

Then, the following command should resolve the issue. :
#
#$ sudo grub-install --recheck /dev/sda

When I get to sudo mount -t ext4 /dev/sda1 /mnt/linux

it tells me:

mount: special device /dev/sdb1 does not exist

Does any have a clue as to why when I do:

sudo fdisk -l /dev/sda

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b4bcf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38882   312319633+  8e  Linux LVM
/dev/sda2           38883       38913      249007+   5  Extended
/dev/sda5           38883       38913      248976   83  Linux
 
Since I see /dev/sda1, I am confused why the command -

sudo mount -t ext4 /dev/sda1 /mnt/linux 

will not work and why I get the error 13 message.

Any help would be great...

---

