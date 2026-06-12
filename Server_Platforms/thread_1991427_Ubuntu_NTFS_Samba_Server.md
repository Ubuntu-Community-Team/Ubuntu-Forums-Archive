---
title: "Ubuntu NTFS Samba Server"
date: 2012-05-30
forum: Server Platforms
---

### Post by ads2996 on 2012-05-30
Hi,

I was wondering if it is possible to mount hard drives at NTFS on ubuntu then set them up as samba shares to access them from windows. Also can Mediatomb, ushare and trabsmission work with ntfs. 

I have at the moment, a 80gb OS drive and 4 1tb to be data drives.

Thanks in advance.

---

### Post by LHammonds on 2012-05-31
Why would you want NTFS?

I know for a fact that ushare works with ext4.  I have an XBOX360 that connects to my Ubuntu 12.04 server running the ushare service (on an ext4 partition inside a logical volume, inside an LVM)...which is contained inside a VirtualBox on my Windows 7 PC. ;)

Linux can create NTFS partitions, just look at the options fdisk provides:

```

 0  Empty           1c  Hidden Win95 FA 70  DiskSecure Mult bb  Boot Wizard hid
 1  FAT12           1e  Hidden Win95 FA 75  PC/IX           be  Solaris boot
 2  XENIX root      24  NEC DOS         80  Old Minix       c1  DRDOS/sec (FAT-
 3  XENIX usr       39  Plan 9          81  Minix / old Lin c4  DRDOS/sec (FAT-
 4  FAT16 <32M      3c  PartitionMagic  82  Linux swap      c6  DRDOS/sec (FAT-
 5  Extended        40  Venix 80286     83  Linux           c7  Syrinx
 6  FAT16           41  PPC PReP Boot   84  OS/2 hidden C:  da  Non-FS data
 7  HPFS/NTFS       42  SFS             85  Linux extended  db  CP/M / CTOS / .
 8  AIX             4d  QNX4.x          86  NTFS volume set de  Dell Utility
 9  AIX bootable    4e  QNX4.x 2nd part 87  NTFS volume set df  BootIt
 a  OS/2 Boot Manag 4f  QNX4.x 3rd part 8e  Linux LVM       e1  DOS access
 b  Win95 FAT32     50  OnTrack DM      93  Amoeba          e3  DOS R/O
 c  Win95 FAT32 (LB 51  OnTrack DM6 Aux 94  Amoeba BBT      e4  SpeedStor
 e  Win95 FAT16 (LB 52  CP/M            9f  BSD/OS          eb  BeOS fs
 f  Win95 Ext'd (LB 53  OnTrack DM6 Aux a0  IBM Thinkpad hi ee  EFI GPT
10  OPUS            54  OnTrackDM6      a5  FreeBSD         ef  EFI (FAT-12/16/
11  Hidden FAT12    55  EZ-Drive        a6  OpenBSD         f0  Linux/PA-RISC b
12  Compaq diagnost 56  Golden Bow      a7  NeXTSTEP        f1  SpeedStor
14  Hidden FAT16 <3 5c  Priam Edisk     a8  Darwin UFS      f4  SpeedStor
16  Hidden FAT16    61  SpeedStor       a9  NetBSD          f2  DOS secondary
17  Hidden HPFS/NTF 63  GNU HURD or Sys ab  Darwin boot     fd  Linux raid auto
18  AST SmartSleep  64  Novell Netware  b7  BSDI fs         fe  LANstep
1b  Hidden Win95 FA 65  Novell Netware  b8  BSDI swap       ff  BBT

```LHammonds

---

### Post by Cheesemill on 2012-05-31
It's possible to mount NTFS drives with Ubuntu and use them pretty much however you want, but if your machine isn't a Windows dual boot then you should really use ext4 instead. Some NTFS problems can only be fixed by running Windows tools on the drives.

---

### Post by arrrghhh on 2012-05-31
> **Cheesemill said:**
> It's possible to mount NTFS drives with Ubuntu and use them pretty much however you want, but if your machine isn't a Windows dual boot then you should really use ext4 instead. Some NTFS problems can only be fixed by running Windows tools on the drives.

This x1000.  When I first built my Linux server, I was lazy and just re-used my NTFS drives.  Well, besides the insane overhead there are definitely a lot of permission issues with NTFS on Linux systems.

Definitely better to get it onto a file system that supports permissions, and is native to Linux.  I went ext4, but keep eying other file systems...

---

