---
title: "Formatting HDD"
date: 2012-02-15
forum: Server Platforms
---

### Post by Bevlar on 2012-02-15
Hi,

I used ddrescue to clone a disk to keep as a backup.


root@ubuntu:~# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c0d0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9365    75216896   83  Linux
/dev/sda2            9365        9726     2905089    5  Extended
/dev/sda5            9365        9726     2905088   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table


As you can see, the original disk (sda) is showing up as 80026361856 bytes
while the backup disk (sdb) is showing up as 80000000000 bytes.

How do I format sdb correctly to make the full 80026361856 bytes available.

Any advice will be greatly appreciated.

---

### Post by Arand on 2012-02-15
sda:
9729 cylinders

sdb:
9726 cylinders

Based on that it looks like sdb is simply a tad smaller than sda.
You may want to use filesystem-aware tools (e.g. fsarchiver) instead of dd, in combination with mbr+table backups to do the cloning; much more effective and flexible (e.g. can go from large to small devices).

---

### Post by Bevlar on 2012-02-15
Hi thanks for the speedy reply and good eye, I missed the cylinder difference.

If I were to continue using ddrescue. would the write fail at the end of the disk cause me problems? The disk will never reach full capacity as it is only running Ubuntu server and a small installation of nagios.

---

### Post by sudodus on 2012-02-15
You have a swap area at the 'end' of the drive, so

- either you change its size on the source, so that it will be within the boundaries of the target (and after that do the same with the extended partition),

- or you delete it, and change the size of the extended partition, make a new swap area. But it will get a new UUID, so you have to edit the file ***/etc/fstab***
```
sudo nano /etc/fstab
```
You can find the UUID with the command
```
sudo blkid
``` but do ***not*** use any citation marks (")

---

### Post by bakegoodz on 2012-02-19
Yes, I did the same thing once, clone a larger drive to a smaller one with ddresue. It causes major problems if the partition tables says the partition goes farther than the physical disk. Not sure my solution works with every type of filesystem, some may have metadata issues that still says its file system is certain size. What I did was delete the partition from the partition table, it can be done with fdisk or cfdisk. Then I used Testdisk scan the drive and it rebuilt a new table that fit the drive. Even if the filesystem freaks out, if may be fixed with the appropriate filesystem repair tool, like fsck. Personally I would boot my disk of Partition Manager Pro and have it fix it. Of course its not open source and costs good money, but it is the best tool I have for partition and cloning issues. Also, good for correcting hdd interface drivers on Windows when switched to other hardware.

---

