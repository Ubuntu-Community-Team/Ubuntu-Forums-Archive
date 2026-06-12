---
title: "Restoring a backup (softRAID1)"
date: 2008-05-27
forum: Server Platforms
---

### Post by Titan8990 on 2008-05-27
I recently reinstalled Ubuntu in order to get softRAID1 going. Before doing so I made a backup of everything using rsync. I issued the following command:

# rsync -a -x / /media/LATITUDE40GB/backup

I had planned to restore the backup from the Ubuntu Live CD (while the filesystem is not mounted). I ran in to the problem of the RAID set only being recognized inside of my installed OS (which I should have thought of ahead of time). 

So I boot into the LiveCD and run the following:

# rsync -a -x /media/LATITUDE40GB/backup /dev/sda1

It tells me that sda1 is not found. And here is my fdisk -l:

```
root@einstein:~# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005c03c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29908   240235978+  fd  Linux raid autodetect
/dev/sda2           29909       30401     3960022+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c1951

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29908   240235978+  fd  Linux raid autodetect
/dev/sdb2   *       29909       30401     3960022+  83  Linux

Disk /dev/md0: 246.0 GB, 246001565696 bytes
2 heads, 4 sectors/track, 60058976 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
```


So I have my full system backup on this USB HDD and I have Ubuntu installed on a software RAID1. How can I go about restoring this backup? 

Will I run in to issues if I try to backup the filesystem while it is mounted? 

All suggestions are appreciated. 

Also any suggestions on a more effective backup/restore method would be excellent.

---

### Post by smileypaul on 2008-05-27
I dont believe you can write directly to /dev/sda1 .. you must mount it somewhere.

```
 
sudo mkdir /media/somename
sudo mount /dev/sda1 /media/somename
rsync -options /source /target

```

---

### Post by Titan8990 on 2008-05-29
Thanks for your input. I have everything worked out. Now for the next issue....

---

