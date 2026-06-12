---
title: "How to add the other half of my primary drive"
date: 2011-09-04
forum: Server Platforms
---

### Post by tark412 on 2011-09-04
Sorry I am fairly new to the server side of this.  I use only command line with no GUI interface.  

Problem is: I have a 1 TB hard drive and during the course of my installation of Ubuntu Server 11.04 I was read a Ubuntu Server book that told me I would get more long term flexibility if I didn't use my entire drive right off the installation.  Now I am running into the problem of not being able to lack of a better term mount the other half of my drive.

command: df -h

Filesystem        Size       Used   Avail    Use%  Mounted on
/dev/mapper/Tark--Server-root
                       456G      1.1G    432G   1%     /
none                 1.3G     208K     1.3G   1%     /dev
none                 1.3G         0       1.3G   0%    /dev/shm
none                 1.3G     596K     1.3G   1%    /var/run
none                 1.3G         0       1.3G   1%   /var/lock
/dev/sda1         228M      23M     194M  11%  /boot

sudo fdisk /dev/sda

Disk /dev/sda: 1000.2GB  1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes /512 bytes
I/O size (minimum/optimal): 512 bytes /512 bytes
Disk identifier: 0x000f0165

   Device  Boot               Start            End             Blocks             Id           System
/dev/sda1   *                      1              32            248832             83          Linux
Partition 1 does not end on a cylinder boundary.
/dev/sda2                         32        121602      976510977              5          Extended
/dev/sda5                         32        121602      976510976            8e          Linux LVM


It is a SATA drive and the only drive connected if that makes any difference.

I don't know how to add the other half of my drive. I know I am not using hardly any space at all.  I am looking for a long term solution so I can add my very large music collection to the other half of the drive.

I have looked through the book that was previously mentioned over and over looking for how to add the other half the drive and that has proved useless.  I have also been unable to find it via the internet.  If anyone could help it would be appreciated.  Thank you in advance.

---

### Post by YesWeCan on 2011-09-04
[http://ubuntuforums.org/showthread.php?p=11212159#post11212159](http://ubuntuforums.org/showthread.php?p=11212159#post11212159)

---

