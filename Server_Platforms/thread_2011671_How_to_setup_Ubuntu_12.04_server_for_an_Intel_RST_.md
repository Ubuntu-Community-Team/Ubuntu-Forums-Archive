---
title: "How to setup Ubuntu 12.04 server for an Intel RST raid5?"
date: 2012-06-27
forum: Server Platforms
---

### Post by michael123456 on 2012-06-27
hello together,
 
i am new with ubuntu and want to setup a private nas with 6TB as RAID5 and using the onboard Intel Rapid Storage functionality of my mainboard.
 
Currently I have setup 4x HDDS with 2TB each in the BIOS to be part of an 6TB raid5 array and I have installed Ubuntu 12.04.
 
But I have discovered some things that sound strange for me: 
 
- In the Intel RST Bios Utility my raid is shown with the status "Inititailize".
- In Ubuntu the raid array is shown as " /dev/mapper/isw_echahhbgdb_Raid"
 
I have not configured any more inside Ubuntu for now. So my question is:
 
Is that normal? Or did I have missed something I have to setup also in Ubuntu? Maybe mdadm or dmraid? What is the best way to setup a raid with Intel RST in Ubuntu?
 
I have also looked into google and other search engines, which gave me some hints with dmraid:
 
```
root@NAS:~# dmraid -s
*** Group superset isw_echahhbgdb
--> Active Subset
name   : isw_echahhbgdb_Raid
size   : 11721073920
stride : 128
type   : raid5_la
status : ok
subsets: 0
devs   : 4
spares : 0
root@NAS:~# dmraid -r
/dev/sdf: isw, "isw_echahhbgdb", GROUP, ok, 3907029166 sectors, data@ 0
/dev/sde: isw, "isw_echahhbgdb", GROUP, ok, 3907029166 sectors, data@ 0
/dev/sdd: isw, "isw_echahhbgdb", GROUP, ok, 3907029166 sectors, data@ 0
/dev/sdc: isw, "isw_echahhbgdb", GROUP, ok, 3907029166 sectors, data@ 0

```
 
fdisk -l results into:
 
```
Disk /dev/mapper/isw_echahhbgdb_Raid: 6001.2 GB, 6001189847040 bytes
255 heads, 63 sectors/track, 729603 cylinders, total 11721073920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
                          Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_echahhbgdb_Raid1               1  4294967295  2147483647+  ee  GPT
Disk /dev/mapper/isw_echahhbgdb_Raid1: 6001.2 GB, 6001189812736 bytes
255 heads, 63 sectors/track, 729603 cylinders, total 11721073853 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2052474d
This doesn't look like a partition table
Probably you selected the wrong device.
                            Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_echahhbgdb_Raid1p1   ?     6579571  1924427647   958924038+  70  DiskSecure Multi-Boot
/dev/mapper/isw_echahhbgdb_Raid1p2   ?  1953251627  3771827541   909287957+  43  Unknown
/dev/mapper/isw_echahhbgdb_Raid1p3   ?   225735265   225735274           5   72  Unknown
/dev/mapper/isw_echahhbgdb_Raid1p4      2642411520  2642463409       25945    0  Empty

```

---

