---
title: "Raid 5 reporting less usable space"
date: 2013-12-08
forum: Server Platforms
---

### Post by stevebu56 on 2013-12-08
I have a Raid 5 array with 3 disks at 2 TB each for a total of 4 TB usable space.  Correct me if I'm wrong.  I partitioned the created array but only created a partition that was 2TB large.  Dunno why I did that.  I'm pretty sure I just used the defaults when creating the partition via fdisk so I don't know why it wouldn't choose the whole array.  What's the best way to extend this partition to cover the entire array?

---

### Post by nerdtron on 2013-12-08
Can you post the outputs of the following commads:

sudo fdisk -l
lsblk
cat /proc/mdstat

---

### Post by stevebu56 on 2013-12-09
```

sudo fdisk -l 
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x46d1d6b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1608572927   804183040    7  HPFS/NTFS/exFAT
/dev/sda3      1608574974  1953523711   172474369    5  Extended
/dev/sda5      1608574976  1667168725    29296875   83  Linux
/dev/sda6      1945665536  1953523711     3929088   82  Linux swap / Solaris
/dev/sda7      1667170304  1945663487   139246592   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0008da25

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907029167  1953513560   83  Linux

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
18 heads, 63 sectors/track, 3445352 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x4d3d7411

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907029167  1953513560   83  Linux

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x676c9fda

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  3907029167  1953513560   83  Linux

Disk /dev/md0: 4000.5 GB, 4000526106624 bytes
2 heads, 3 sectors/track, 1302254592 cylinders, total 7813527552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x49576c0e

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1            2048  4294967294  2147482623+  83  Linux

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x5bf17d09

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048  3907029167  1953513560   83  Linux

Disk /dev/sdf: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bd002

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           2    31266815    15633407    b  W95 FAT32

```

```

lsblk 
NAME        MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda           8:0    0 931.5G  0 disk  
&#9500;&#9472;sda1        8:1    0   100M  0 part  
&#9500;&#9472;sda2        8:2    0   767G  0 part  /media/WIN1TB
&#9500;&#9472;sda3        8:3    0     1K  0 part  
&#9500;&#9472;sda5        8:5    0    28G  0 part  /
&#9500;&#9472;sda6        8:6    0   3.8G  0 part  [SWAP]
&#9492;&#9472;sda7        8:7    0 132.8G  0 part  /home
sdb           8:16   0   1.8T  0 disk  
&#9492;&#9472;sdb1        8:17   0   1.8T  0 part  
  &#9492;&#9472;md0       9:0    0   3.7T  0 raid5 
    &#9492;&#9472;md0p1 259:0    0     2T  0 md    /media/SEAGRAID
sdc           8:32   0   1.8T  0 disk  
&#9492;&#9472;sdc1        8:33   0   1.8T  0 part  
  &#9492;&#9472;md0       9:0    0   3.7T  0 raid5 
    &#9492;&#9472;md0p1 259:0    0     2T  0 md    /media/SEAGRAID
sdd           8:48   0   1.8T  0 disk  
&#9492;&#9472;sdd1        8:49   0   1.8T  0 part  /media/SEAG2TB3
sde           8:64   0   1.8T  0 disk  
&#9492;&#9472;sde1        8:65   0   1.8T  0 part  
  &#9492;&#9472;md0       9:0    0   3.7T  0 raid5 
    &#9492;&#9472;md0p1 259:0    0     2T  0 md    /media/SEAGRAID
sdf           8:80   1  14.9G  0 disk  
&#9492;&#9472;sdf1        8:81   1  14.9G  0 part  /media/16GB SANDIS

```

```

cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sde1[3] sdc1[1] sdb1[0]
      3906763776 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
      
unused devices: <none>

```

---

### Post by CharlesA on 2013-12-09
You need to use GPT not MBR for the disk format.

Check this out:
[http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm](http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm)

---

### Post by stevebu56 on 2013-12-09
I read through the link about using GPT.  Will I be able to keep the filesystem intact and just delete & recreate the partition with GPT or will I lose all my data and have to start from scratch?

---

### Post by CharlesA on 2013-12-09
> **stevebu56 said:**
> I read through the link about using GPT.  Will I be able to keep the filesystem intact and just delete & recreate the partition with GPT or will I lose all my data and have to start from scratch?

The only way I know of converting from an MRB to GPT partition is to recreate the partition, which means backing up all your data and restoring it once the partition is recreated and the array is resynced. On the plus side, you'll be able to make the partition fill the entire drive.

---

### Post by stevebu56 on 2013-12-09
Ok, thanks for the help.  I'll start the backing up process.  Ugh.

---

### Post by stevebu56 on 2013-12-13
With 'df -h' it's reporting that my array has 3.6TB of usable space.  Is .4TB of overhead correct?

---

### Post by CharlesA on 2013-12-13
> **stevebu56 said:**
> With 'df -h' it's reporting that my array has 3.6TB of usable space.  Is .4TB of overhead correct?

Yep. Blame the whole 1KB = 1000 bytes, not 1024 bytes thing.

---

