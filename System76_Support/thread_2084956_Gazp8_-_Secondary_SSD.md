---
title: "Gazp8 - Secondary SSD"
date: 2012-11-16
forum: System76 Support
---

### Post by IntoFlow on 2012-11-16
I'm loving my Gazelle Professional. I do a lot of photo/video editing, so I've a need for lots of space.

I've one 512GB SSD as my main hard drive, and I've a secondary 128GB SSD. /dev/sda is the main 512GB hard drive, and /dev/sdb is the secondary 128GB hard drive.

However, I haven't yet quite figured out the secondary SSD.

After running *sudo fdisk -l* here's what I get:

> Disk /dev/sda: 512.1 GB, 512110190592 bytes
255 heads, 63 sectors/track, 62260 cylinders, total 1000215216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008c868

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2148   992685546   496341699+  83  Linux
/dev/sda2       992685547  1000215215     3764834+   5  Extended
/dev/sda5       992685548  1000215215     3764834   83  Linux

Disk /dev/sdb: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
So the 128 has yet to be used. Where do I go from here? I would like it to be automatically mounted when I start the computer... but, again, have yet to figure that out.

Thanks.

---

### Post by pqwoerituytrueiwoq on 2012-11-16
edit your /etc/fstab file, it it is a *ext4* partition on it do it like this
```
UUID=aa92d082-0e37-4e70-b696-7198daf30c62 /mnt/storage           ext4    defaults        0       2
```change the aa92d082-0e37-4e70-b696-7198daf30c62 to what [gparted]("apt:gparted") shows for the uuid (right click the partition-> information)
your drive will show up in */mnt/storage*
after you run *sudo mount -a* or reboot

---

### Post by IntoFlow on 2012-11-16
The only thing I'm seeing in fstab is

> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=6fb59d06-ec00-44f4-abcc-0da0f018be93    /    ext4    discard,errors=remount-ro    0    1    # /dev/sda1
# swap was on /dev/sdb5 during installation
UUID=616eaa19-299e-479b-8dcf-dfc36593f63a    none    swap    sw    0    0    # /dev/sda5

---

### Post by oldfred on 2012-11-17
If you have not formatted it, then you have to use gparted to format it.

I think with pqwoerituytrueiwoq's instruction you have to make the mount point first.

sudo mkdir /mnt/storage

Another set of similar instructions.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
    
More info in general:
       [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by IntoFlow on 2012-11-17
Thanks mate, it was easier than I thought. ANd I also managed to upgrade the firmware of the second SSD to the latest version as well while I was at it.

Cheers.

---

