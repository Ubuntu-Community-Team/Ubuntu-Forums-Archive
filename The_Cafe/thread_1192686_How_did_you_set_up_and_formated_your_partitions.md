---
title: "How did you set up and formated your partitions?"
date: 2009-06-20
forum: The Cafe
---

### Post by jersoncito on 2009-06-20
How did you set up and formated your partitions?

These are mine:
(160 GB hard drive)

Primary

Windows 25 GB ntfs

Boot 300 MB ext3 (Ubuntu)

Logical
/    700 MB jfs
/opt  300 MB jfs
/var   2.5 GB jfs
/usr   4.5 GB jfs
/tmp    9 GB jfs
/home  110 GB xfs

I'm still using Ubuntu Hardy since April 2008. The reason why I gave 9 GB to /tmp is because with less of that, I was not able to copy DVD-DL. I thought Ubuntu it was going to take the space from /home, but it was not the case.

---

### Post by gn2 on 2009-06-20
/ 148gb ext3

swap 1gb

---

### Post by Regenweald on 2009-06-20
WD 120 GB | sda1 8GB ext4 - '/' | sda2 96GB ext4 - '/home'
WD 120 GB | sdb1 8GB ntfs - 'XP' | sdb2 100 GB ntfs media dump
SG 250 GB  | sdc1 250 GB ext3 Logical

This is the new setup, recently messed up grub2 so I re-organised.

---

### Post by CharmyBee on 2009-06-20
20GB Windows XP 32bit NTFS
20GB Windows XP 64bit NTFS
20GB Ubuntu 8.10 32bit ext3
20GB Ubuntu 9.04 64bit ext3
280GB Data NTFS
460GB Data NTFS
No swap partition

---

### Post by Dimitriid on 2009-06-20
```
Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000b0dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       90922   730330933+  83  Linux
/dev/sda2           90923       91201     2241067+   5  Extended
/dev/sda5           90923       91201     2241036   82  Linux swap / Solaris
```

---

### Post by sahabcse on 2009-06-20
past the o/p of

cd /tmp
du -csh ./*

---

### Post by raymondh on 2009-06-20
2 HD's

Each disk contains /, /data, SWAP

Each disk has a different release of Ubuntu.  That way, I can tweak, work on the newer release knowing that if I bork it, I can always resort to the older, tested, stable release.  When I get a new version, I just install over the older one and so goes the cycle.

All my personal files are in an external easily accessed by either version.

---

### Post by jonian_g on 2009-06-20
HDD: 320 GB

/ - 10 GB ext4
/home - 310 GB ext3

No swap partition since I have 4GB of Ram.

---

### Post by pbpersson on 2009-06-20
Main Ubuntu Desktop:

```
sda1  7.5 GB  Swap
sda2  420 GB  Ext3  /
sda3  270 GB  Ext3  /home

sdb1  300 GB  Ext3  /home/phil/MyData/SATA2

sdc1  300 GB  EXt3  /home/phil/MyData/SATA3
```


The mount points for my SATA2 and SATA3 drives did not have very creative names, but I wanted them to mean something.  On the main drive I have a directory /home/phil/MyData/SATA1 and I was going to share the MyData directory on the network but never got that far.

---

### Post by camper365 on 2009-06-20
40 GB HDD

11 GB NTFS -- Windows
2 GB ext4 -- /
2 GB ext4 -- /var
128 MB ext4 -- /boot
6 GB ext4 -- /usr
14 GB ext4 -- /home
2.5 GB swap

---

### Post by starcannon on 2009-06-20
Disk /dev/sdx: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: mumbojumbo

   Device Boot      Start         End      Blocks   Id  System
/dev/sdx1               1        2490    20000893+   7  HPFS/NTFS
/dev/sdx2   *        2491        4922    19535040   83  Linux
/dev/sdx3            4923       30401   204660067+  83  Linux
/dev/sdy3           30153       30401     2000092+  82  Linux swap / Solaris

Thats the basics of a dual boot setup, and when commercial gaming finally arrives, the NTFS partition will disappear from my setup. Currently my partition sizes are:

/dev/sdx1 /windowsXP 30gb
/dev/sdx2 / 20gb
/dev/sdx3 /home Whats left of the first drive.
/dev/sdy3 /swap is set equal to my amount of installed ram.

At some point I think I'll be changing things up a bit, but for now this basic pattern is what works for me.

---

### Post by JordyD on 2009-06-20
```
Model: ATA WDC WD1600JS-98M (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      512B    41.1MB  41.1MB  primary  ext2         boot 
 2      41.1MB  1094MB  1053MB  primary  linux-swap        
 3      1094MB  53.5GB  52.4GB  primary  ext3              
 4      53.5GB  160GB   107GB   primary  ext3              
```

1 = /boot
2 = swap
3 = /home
4 = /

---

### Post by dragos240 on 2009-06-20
I used parted magic

---

### Post by Eisenwinter on 2009-06-20
sdb1 - NTFS, Windows XP, 60GB
sdb2 - Ext2, Linux /boot, 4GB
sdb3 - Ext4, Linux root partition, 100GB
sdb4 - Ext4, Linux /home, rest of sdb disk in size (about 350GB or so)

and sda1, a sole Ext4 partition, hosts /Music - 80GB

---

### Post by mali2297 on 2009-06-20
Primary:
20 GB Windows ntfs
60 MB /boot ext2
35 GB /data xfs

Logical:
750 MB swap
10 GB / ext3
10 GB unformated
1 GB /opt ext3

---

### Post by xpod on 2009-06-20
I`ve had 2 drives in my main Desktop since i began using Ubuntu.The drives & machines have changed quite a few times but the drive layouts themselves have stayed pretty much the same.Except for the very first week when there was still a NTFS drive,which quickly shrunk to a partition....which then disappeared completely.:D

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea55ea55

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1946    15631213+  83  Linux
/dev/sda2            1947       24053   177574477+  83  Linux
/dev/sda3           24054       24321     2152710   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004280c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3647    29294496   83  Linux
/dev/sdb2            3648       19209   125001765   83  Linux
/dev/sdb3           19210       19457     1992060   82  Linux swap / Solaris

```

---

### Post by FuturePilot on 2009-06-20
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e236e23

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8552    68693908+   7  HPFS/NTFS
/dev/sda2            8553       11400    22876560   83  Linux
/dev/sda3           11401       18366    55954395    5  Extended
/dev/sda4           18367       19457     8763457+   7  HPFS/NTFS
/dev/sda5           17921       18366     3582463+  82  Linux swap / Solaris
/dev/sda6           11401       17920    52371837   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb4a53fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

```

Basically 65GB for Vista (I can't for the life of me figure out what is taking up 40GB of that :???:
8GB for this recovery partition
20GB for / ext3
50GB for /home ext3
3.5GB for swap
500GB ext3 on my external drive.

---

