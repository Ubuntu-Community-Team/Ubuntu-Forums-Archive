---
title: "New Virtual Disk in Ubuntu 12.04.4"
date: 2014-02-17
forum: Server Platforms
---

### Post by JnPson on 2014-02-17
I have installed Ubuntu Server 12.04.4 in virtualbox and need to add more disk space. 
I somhow forgot how to add a new virtual disk to my Ubuntu server 12.04.4. 
I've added a new 150 GB virtual disk in virtualbox and I can see the disk with
```
fdisk -l
``` but not when I run 
```
blkid
```
What am I missing?

---

### Post by sudodus on 2014-02-17
Try ```
sudo blkid -c /dev/null
``` which is described in ```
man blkid
```

```
       -c cachefile
              Read from cachefile instead of reading from the default cache file  /etc/blkid.tab.   If
              you  want  to start with a clean cache (i.e. don't report devices previously scanned but
              not necessarily available at this time), specify /dev/null.

```

It could also be that you have no partition yet on the new virtual disk. blkid sees partitions (not disks).

---

### Post by JnPson on 2014-02-17
I don't think virtualbox has formatted the disk, so that might be the cause. Then I need to know how I can format the drive through the terminal.
fdisk -l shows
```
jon@dc01:~$ sudo fdisk -l

Disk /dev/sda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e6b06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758    16775167     8136705    5  Extended
/dev/sda5          501760    16775167     8136704   8e  Linux LVM

**Disk /dev/sdb: 161.1 GB, 161061273600 bytes**
255 heads, 63 sectors/track, 19581 cylinders, total 314572800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

**Disk /dev/sdb doesn't contain a valid partition table**

Disk /dev/mapper/dc01--vg-root: 7763 MB, 7763656704 bytes
255 heads, 63 sectors/track, 943 cylinders, total 15163392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/dc01--vg-root doesn't contain a valid partition table

Disk /dev/mapper/dc01--vg-swap_1: 532 MB, 532676608 bytes
255 heads, 63 sectors/track, 64 cylinders, total 1040384 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/dc01--vg-swap_1 doesn't contain a valid partition table


```

---

### Post by sudodus on 2014-02-17
You can try fdisk or parted (or cfdisk, which is quite simple to use and might be able to do what you want).

---

