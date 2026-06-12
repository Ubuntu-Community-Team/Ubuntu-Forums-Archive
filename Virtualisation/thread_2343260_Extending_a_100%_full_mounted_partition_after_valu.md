---
title: "Extending a 100% full mounted partition after valume 50gb in VMware (no GUI)"
date: 2016-11-14
forum: Virtualisation
---

### Post by Aphexlog on 2016-11-14
Hello all,

I have just added 50GB to a vmware (Ubuntu 14.04) server and I need to figure out how to extend the full volume to utilize the newly added disk space.
There was an allocated 100GB prior to me adding the additional 50GB.
Here is the lsblk output:

```
vmadmin@Docker-Registry:/dev$ lsblk
NAME                                   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                                      8:0    0   150G  0 disk
&#9500;&#9472;sda1                                   8:1    0   243M  0 part /boot
&#9500;&#9472;sda2                                   8:2    0     1K  0 part
&#9492;&#9472;sda5                                   8:5    0  99.8G  0 part
  &#9500;&#9472;Docker--Registry--vg-root (dm-0)   252:0    0  91.8G  0 lvm  /
  &#9492;&#9472;Docker--Registry--vg-swap_1 (dm-1) 252:1    0     8G  0 lvm  [SWAP]
sr0                                     11:0    1   572M  0 rom

```

The following is the fdisk -l output:
```
vmadmin@Docker-Registry:/dev$ sudo fdisk -l


Disk /dev/sda: 161.1 GB, 161061273600 bytes
255 heads, 63 sectors/track, 19581 cylinders, total 314572800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006413b


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   209713151   104605697    5  Extended
/dev/sda5          501760   209713151   104605696   8e  Linux LVM


Disk /dev/mapper/Docker--Registry--vg-root: 98.5 GB, 98507423744 bytes
255 heads, 63 sectors/track, 11976 cylinders, total 192397312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/Docker--Registry--vg-root doesn't contain a valid partition table


Disk /dev/mapper/Docker--Registry--vg-swap_1: 8585 MB, 8585740288 bytes
255 heads, 63 sectors/track, 1043 cylinders, total 16769024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/Docker--Registry--vg-swap_1 doesn't contain a valid partition table

```
As you can see, the full space is located at the Docker--Registry--vg-root mount point - this is what I am trying to extend to use an additional 50GB.
So, my question is how do I extend the 100Gb 'Docker--Registry--vg-root' mount point to 150GB?

Thanks in advance.

---

### Post by howefield on 2016-11-14
Moved to the "*Virtualisation*" forum for a better fit.

---

