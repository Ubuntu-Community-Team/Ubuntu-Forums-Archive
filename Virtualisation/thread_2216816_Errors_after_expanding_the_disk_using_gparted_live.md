---
title: "Errors after expanding the disk using gparted live 0.18.X"
date: 2014-04-14
forum: Virtualisation
---

### Post by harishbayyavarapu on 2014-04-14
I cannot start my Ubuntu after expanding the harddisk. Installed the Ubuntu 12.04 with 30GB space and I ran out of space, so I used gparted live to expand the disk space. After doing that my partition table got corrupted I guess and I am not able to boot to my environment. VirtualBox keeps crashing, after several attempts, finally Ubuntu boots in read-only mode. I am not sure how to fix this. Please help me.

```
sudo LANG=C sfdisk -d /dev/sda > sfdisk.txt
# partition table of /dev/sda
unit: sectors


/dev/sda1 : start=     2048, size= 67102720, Id=83, bootable
/dev/sda2 : start= 67104768, size= 16781312, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0

```

And I get this error
```
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


sfdisk: ERROR: sector 67104768 does not have an msdos signature

```

```

sudo LANG=C fdisk -lu
sudo: unable to open /var/lib/sudo/portaldev/2: Read-only file system
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)


Disk /dev/sda: 42.9 GB, 42949672960 bytes
255 heads, 63 sectors/track, 5221 cylinders, total 83886080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00020bb7


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    67104767    33551360   83  Linux
/dev/sda2        67104768    83886079     8390656    5  Extended


```

If I boot into gparted live, I get error 
I am stuck doing nothing, I can't work because of this issue. Please help me resolve this.

---

### Post by heiko_s on 2014-04-16
After expanding with e.g. gparted, you also need to resize the file system:

```
sudo resize2fs /dev/sda1
```

Make sure to replace sda1 with the partition you actually need to resize.

The above command should be run from a life Linux image (or gparted rescue disc).

---

