---
title: "install fails, too many (primary partitions)"
date: 2013-10-20
forum: Server Platforms
---

### Post by enboig on 2013-10-20
I am installing 2 new 2TB discs on my server (dell RS200 using SAS); but they never get to boot. I tried disabling hardware raid and installing ubunt desktop on one of the disk, but it complains too many primary partitions on disk.

I checked (fdisk, gparted, ...) and there aren't any partitions on disk. I also tried creating the partition table as GPT but the error continues.

Any hint/help?

thanks

---

### Post by hawkmage on 2013-10-20
If these drives have been used before in other system especially NAS hardware you can have some info on the drive that is confusing the installer.  One thing that has helped me on these occasions is to use a Linux Recovery or Live CD/DVD and wipe the beginning of the drive using the dd command with /dev/zero as input and the drive as output.  I usually wipe the first few megabytes of the drive to be sure.  

Here is the command that needs to be run as root but be careful it can wipe the first 10MB of a drive in seconds.
```
dd if=/dev/zero bs=512 count=20480 of=/dev/sdX
```
You will have to replace the sdX with the drive you want to wipe.

---

### Post by enboig on 2013-10-21
I tried dd, but only the first part of the disk, and didn't worked.

Finally i installed on a 3rd disk, and afterwards created the raid and mounted as home.

---

