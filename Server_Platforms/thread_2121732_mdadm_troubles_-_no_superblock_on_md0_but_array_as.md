---
title: "mdadm troubles - no superblock on md0 but array assembles"
date: 2013-03-02
forum: Server Platforms
---

### Post by Silicon Knight on 2013-03-02
Hi All, I'm having a bit of a time with MDADM.  Basically I have a RAID6 system setup w/ 10 hard drives (1.5GB).  Last night I had a failed drive and i accidentally failed out the wrong drive trying to fix it.  Right now I can get the array to assemble successfully but I cant read anything off of md0, it can't mount either.  Here is the output of a few command:

**mdadm --examine /dev/md0**
```
 
mdadm: No md superblock detected on /dev/md0.
```

[B]# mdadm --assemble --scan -v
[/B]```
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdj1 is not one of /dev/sdb1,/dev/sdc1,/dev/sdd1,/dev/sde1,/dev/sdf1,/dev/sdg1,/dev/sdh1,/dev/sdi1,dev/sdj1,/dev/sdk1
mdadm: /dev/sdk1 is identified as a member of /dev/md0, slot 9.
mdadm: /dev/sdi1 is identified as a member of /dev/md0, slot 7.
mdadm: /dev/sdh1 is identified as a member of /dev/md0, slot 6.
mdadm: /dev/sdg1 is identified as a member of /dev/md0, slot 5.
mdadm: /dev/sdf1 is identified as a member of /dev/md0, slot 4.
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot 3.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 0.
mdadm: added /dev/sdc1 to /dev/md0 as 1
mdadm: added /dev/sdd1 to /dev/md0 as 2
mdadm: added /dev/sde1 to /dev/md0 as 3
mdadm: added /dev/sdf1 to /dev/md0 as 4
mdadm: added /dev/sdg1 to /dev/md0 as 5
mdadm: added /dev/sdh1 to /dev/md0 as 6
mdadm: added /dev/sdi1 to /dev/md0 as 7
mdadm: no uptodate device for slot 8 of /dev/md0
mdadm: added /dev/sdk1 to /dev/md0 as 9
mdadm: added /dev/sdb1 to /dev/md0 as 0
mdadm: /dev/md0 has been started with 9 drives (out of 10).

```

**# mdadm --detail /dev/md0**
```
/dev/md0:
        Version : 1.2
  Creation Time : Sat Mar  2 19:06:59 2013
     Raid Level : raid6
     Array Size : 11715731456 (11172.99 GiB 11996.91 GB)
  Used Dev Size : 1464466432 (1396.62 GiB 1499.61 GB)
   Raid Devices : 10
  Total Devices : 9
    Persistence : Superblock is persistent


    Update Time : Sat Mar  2 19:06:59 2013
          State : clean, degraded 
 Active Devices : 9
Working Devices : 9
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : AR-NAS:0  (local to host AR-NAS)
           UUID : 267d0d47:387d7113:fe31ac5c:9add924e
         Events : 0


    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       81        4      active sync   /dev/sdf1
       5       8       97        5      active sync   /dev/sdg1
       6       8      113        6      active sync   /dev/sdh1
       7       8      129        7      active sync   /dev/sdi1
       8       0        0        8      removed
       9       8      161        9      active sync   /dev/sdk1

```

**fdisk -l /dev/md0**
```
Disk /dev/md0: 11998.0 GB, 11997982752768 bytes
2 heads, 4 sectors/track, -1365772288 cylinders, total 23433560064 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 1048576 bytes / 8388608 bytes

```

**# mdadm --examine /dev/sd[bcdefghijk]1**
```

/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 267d0d47:387d7113:fe31ac5c:9add924e
           Name : AR-NAS:0  (local to host AR-NAS)
  Creation Time : Sat Mar  2 19:06:59 2013
     Raid Level : raid6
   Raid Devices : 10


 Avail Dev Size : 2928934878 (1396.63 GiB 1499.61 GB)
     Array Size : 11715731456 (11172.99 GiB 11996.91 GB)
  Used Dev Size : 2928932864 (1396.62 GiB 1499.61 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : d4dc6bbc:50da526b:4cb3d499:55a5a6b7


    Update Time : Sat Mar  2 20:27:21 2013
       Checksum : 4dadf65e - correct
         Events : 2


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 0
   Array State : AAAAAAAA.A ('A' == active, '.' == missing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 267d0d47:387d7113:fe31ac5c:9add924e
           Name : AR-NAS:0  (local to host AR-NAS)
  Creation Time : Sat Mar  2 19:06:59 2013
     Raid Level : raid6
   Raid Devices : 10


 Avail Dev Size : 2928934878 (1396.63 GiB 1499.61 GB)
     Array Size : 11715731456 (11172.99 GiB 11996.91 GB)
  Used Dev Size : 2928932864 (1396.62 GiB 1499.61 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : f2747d0c:1310f714:d4a076a8:0fc2741e


    Update Time : Sat Mar  2 20:27:21 2013
       Checksum : bcd3ce80 - correct
         Events : 2


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 1
   Array State : AAAAAAAA.A ('A' == active, '.' == missing)

/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 267d0d47:387d7113:fe31ac5c:9add924e
           Name : AR-NAS:0  (local to host AR-NAS)
  Creation Time : Sat Mar  2 19:06:59 2013
     Raid Level : raid6
   Raid Devices : 10


 Avail Dev Size : 2928934878 (1396.63 GiB 1499.61 GB)
     Array Size : 11715731456 (11172.99 GiB 11996.91 GB)
  Used Dev Size : 2928932864 (1396.62 GiB 1499.61 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 354ad7b0:93b718cb:e0147b71:35ac114a


    Update Time : Sat Mar  2 20:27:21 2013
       Checksum : bf0a978 - correct
         Events : 2


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 2
   Array State : AAAAAAAA.A ('A' == active, '.' == missing)
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 267d0d47:387d7113:fe31ac5c:9add924e
           Name : AR-NAS:0  (local to host AR-NAS)
  Creation Time : Sat Mar  2 19:06:59 2013
     Raid Level : raid6
   Raid Devices : 10


 Avail Dev Size : 2930012160 (1397.14 GiB 1500.17 GB)
     Array Size : 11715731456 (11172.99 GiB 11996.91 GB)
  Used Dev Size : 2928932864 (1396.62 GiB 1499.61 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 5c01ec81:233e0df7:50e30601:751d142e


    Update Time : Sat Mar  2 20:27:21 2013
       Checksum : 7c989701 - correct
         Events : 2


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 3
   Array State : AAAAAAAA.A ('A' == active, '.' == missing)

/dev/sdf1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 267d0d47:387d7113:fe31ac5c:9add924e
           Name : AR-NAS:0  (local to host AR-NAS)
  Creation Time : Sat Mar  2 19:06:59 2013
     Raid Level : raid6
   Raid Devices : 10


 Avail Dev Size : 2928934878 (1396.63 GiB 1499.61 GB)
     Array Size : 11715731456 (11172.99 GiB 11996.91 GB)
  Used Dev Size : 2928932864 (1396.62 GiB 1499.61 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 80fe6eea:78c2f69b:d5321b3d:a22507c0


    Update Time : Sat Mar  2 20:27:21 2013
       Checksum : 57fc000c - correct
         Events : 2


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 4
   Array State : AAAAAAAA.A ('A' == active, '.' == missing)
/dev/sdg1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 267d0d47:387d7113:fe31ac5c:9add924e
           Name : AR-NAS:0  (local to host AR-NAS)
  Creation Time : Sat Mar  2 19:06:59 2013
     Raid Level : raid6
   Raid Devices : 10


 Avail Dev Size : 2928934845 (1396.62 GiB 1499.61 GB)
     Array Size : 11715731456 (11172.99 GiB 11996.91 GB)
  Used Dev Size : 2928932864 (1396.62 GiB 1499.61 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 3b7cc21a:5d692236:cabb08cc:0f432714


    Update Time : Sat Mar  2 20:27:21 2013
       Checksum : 588caed - correct
         Events : 2


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 5
   Array State : AAAAAAAA.A ('A' == active, '.' == missing)

/dev/sdh1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 267d0d47:387d7113:fe31ac5c:9add924e
           Name : AR-NAS:0  (local to host AR-NAS)
  Creation Time : Sat Mar  2 19:06:59 2013
     Raid Level : raid6
   Raid Devices : 10


 Avail Dev Size : 2928934845 (1396.62 GiB 1499.61 GB)
     Array Size : 11715731456 (11172.99 GiB 11996.91 GB)
  Used Dev Size : 2928932864 (1396.62 GiB 1499.61 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : d0ec6626:9a77353c:a2e24a9c:bd156c3c


    Update Time : Sat Mar  2 20:27:21 2013
       Checksum : fc74346 - correct
         Events : 2


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 6
   Array State : AAAAAAAA.A ('A' == active, '.' == missing)
/dev/sdi1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 267d0d47:387d7113:fe31ac5c:9add924e
           Name : AR-NAS:0  (local to host AR-NAS)
  Creation Time : Sat Mar  2 19:06:59 2013
     Raid Level : raid6
   Raid Devices : 10


 Avail Dev Size : 2928933532 (1396.62 GiB 1499.61 GB)
     Array Size : 11715731456 (11172.99 GiB 11996.91 GB)
  Used Dev Size : 2928932864 (1396.62 GiB 1499.61 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 65494853:b588c0fa:9a78190f:83f67a32


    Update Time : Sat Mar  2 20:27:21 2013
       Checksum : 64112294 - correct
         Events : 2


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 7
   Array State : AAAAAAAA.A ('A' == active, '.' == missing)

/dev/sdj1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 267d0d47:387d7113:fe31ac5c:9add924e
           Name : AR-NAS:0  (local to host AR-NAS)
  Creation Time : Sat Mar  2 19:06:59 2013
     Raid Level : raid6
   Raid Devices : 10


 Avail Dev Size : 2928934810 (1396.62 GiB 1499.61 GB)
     Array Size : 11715731456 (11172.99 GiB 11996.91 GB)
  Used Dev Size : 2928932864 (1396.62 GiB 1499.61 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 630c017e:7de28e7f:5aca24e5:8e684bdc


    Update Time : Sat Mar  2 19:06:59 2013
       Checksum : 93adf592 - correct
         Events : 0


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 8
   Array State : AAAAAAAAAA ('A' == active, '.' == missing)
/dev/sdk1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 267d0d47:387d7113:fe31ac5c:9add924e
           Name : AR-NAS:0  (local to host AR-NAS)
  Creation Time : Sat Mar  2 19:06:59 2013
     Raid Level : raid6
   Raid Devices : 10


 Avail Dev Size : 2928934844 (1396.62 GiB 1499.61 GB)
     Array Size : 11715731456 (11172.99 GiB 11996.91 GB)
  Used Dev Size : 2928932864 (1396.62 GiB 1499.61 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 1b00c2c5:07423417:ad2f68dc:58decccf


    Update Time : Sat Mar  2 20:27:21 2013
       Checksum : 5d9f36a7 - correct
         Events : 2


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 9
   Array State : AAAAAAAA.A ('A' == active, '.' == missing)

```

**# cat /proc/mdstat**
```
Personalities : [raid6] [raid5] [raid4] 
md0 : active raid6 sdb1[0] sdk1[9] sdi1[7] sdh1[6] sdg1[5] sdf1[4] sde1[3] sdd1[2] sdc1[1]
      11715731456 blocks super 1.2 level 6, 512k chunk, algorithm 2 [10/9] [UUUUUUUU_U]
      
unused devices: <none>

```

I figure I need some serious help by you guys any help with this would be greatly appreciated.  I really hope I can get my photos back, got some family pictures I have not done a recent backup of yet :(

Thanks all!

---

### Post by Silicon Knight on 2013-03-02
One more thing, not sure if its useful or not but if I remove the /etc/mdadm.conf file I get the following when I assemble:

**# mdadm --assemble --scan -v**
```
mdadm: looking for devices for further assemblymdadm: no recogniseable superblock on /dev/dm-2
mdadm: no recogniseable superblock on /dev/dm-1
mdadm: no recogniseable superblock on /dev/dm-0
mdadm: no RAID superblock on /dev/sdk
mdadm: no RAID superblock on /dev/sdj
mdadm: no RAID superblock on /dev/sdi
mdadm: no RAID superblock on /dev/sdh
mdadm: no RAID superblock on /dev/sdg
mdadm: cannot open device /dev/sr0: No medium found
mdadm: no RAID superblock on /dev/sdf
mdadm: no RAID superblock on /dev/sde
mdadm: no RAID superblock on /dev/sdd
mdadm: no RAID superblock on /dev/sdc
mdadm: no RAID superblock on /dev/sdb
mdadm: no RAID superblock on /dev/sda2
mdadm: no RAID superblock on /dev/sda1
mdadm: no RAID superblock on /dev/sda
mdadm: /dev/sdk1 is identified as a member of /dev/md/0, slot 9.
mdadm: /dev/sdj1 is identified as a member of /dev/md/0, slot 8.
mdadm: /dev/sdi1 is identified as a member of /dev/md/0, slot 7.
mdadm: /dev/sdh1 is identified as a member of /dev/md/0, slot 6.
mdadm: /dev/sdg1 is identified as a member of /dev/md/0, slot 5.
mdadm: /dev/sdf1 is identified as a member of /dev/md/0, slot 4.
mdadm: /dev/sde1 is identified as a member of /dev/md/0, slot 3.
mdadm: /dev/sdd1 is identified as a member of /dev/md/0, slot 2.
mdadm: /dev/sdc1 is identified as a member of /dev/md/0, slot 1.
mdadm: /dev/sdb1 is identified as a member of /dev/md/0, slot 0.
mdadm: added /dev/sdc1 to /dev/md/0 as 1
mdadm: added /dev/sdd1 to /dev/md/0 as 2
mdadm: added /dev/sde1 to /dev/md/0 as 3
mdadm: added /dev/sdf1 to /dev/md/0 as 4
mdadm: added /dev/sdg1 to /dev/md/0 as 5
mdadm: added /dev/sdh1 to /dev/md/0 as 6
mdadm: added /dev/sdi1 to /dev/md/0 as 7
mdadm: added /dev/sdj1 to /dev/md/0 as 8 (possibly out of date)
mdadm: added /dev/sdk1 to /dev/md/0 as 9
mdadm: added /dev/sdb1 to /dev/md/0 as 0
mdadm: /dev/md/0 has been started with 9 drives (out of 10).
mdadm: looking for devices for further assembly
mdadm: looking for devices for further assembly
mdadm: no recogniseable superblock on /dev/md/0
mdadm: no recogniseable superblock on /dev/dm-2
mdadm: no recogniseable superblock on /dev/dm-1
mdadm: no recogniseable superblock on /dev/dm-0
mdadm: /dev/sdk1 is busy - skipping
mdadm: Cannot assemble mbr metadata on /dev/sdk
mdadm: no RAID superblock on /dev/sdj
mdadm: /dev/sdi1 is busy - skipping
mdadm: no RAID superblock on /dev/sdi
mdadm: /dev/sdh1 is busy - skipping
mdadm: no RAID superblock on /dev/sdh
mdadm: /dev/sdg1 is busy - skipping
mdadm: no RAID superblock on /dev/sdg
mdadm: cannot open device /dev/sr0: No medium found
mdadm: /dev/sdf1 is busy - skipping
mdadm: no RAID superblock on /dev/sdf
mdadm: /dev/sde1 is busy - skipping
mdadm: no RAID superblock on /dev/sde
mdadm: /dev/sdd1 is busy - skipping
mdadm: no RAID superblock on /dev/sdd
mdadm: /dev/sdc1 is busy - skipping
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdb1 is busy - skipping
mdadm: no RAID superblock on /dev/sdb
mdadm: no RAID superblock on /dev/sda2
mdadm: no RAID superblock on /dev/sda1
mdadm: no RAID superblock on /dev/sda
mdadm: /dev/sdj1 is identified as a member of /dev/md/0_0, slot 8.
mdadm: no uptodate device for slot 0 of /dev/md/0_0
mdadm: no uptodate device for slot 1 of /dev/md/0_0
mdadm: no uptodate device for slot 2 of /dev/md/0_0
mdadm: no uptodate device for slot 3 of /dev/md/0_0
mdadm: no uptodate device for slot 4 of /dev/md/0_0
mdadm: no uptodate device for slot 5 of /dev/md/0_0
mdadm: no uptodate device for slot 6 of /dev/md/0_0
mdadm: no uptodate device for slot 7 of /dev/md/0_0
mdadm: no uptodate device for slot 9 of /dev/md/0_0
mdadm: added /dev/sdj1 to /dev/md/0_0 as 8
mdadm: /dev/md/0_0 assembled from 1 drive - not enough to start the array.
mdadm: looking for devices for further assembly
mdadm: /dev/sdk1 is busy - skipping
mdadm: /dev/sdi1 is busy - skipping
mdadm: /dev/sdh1 is busy - skipping
mdadm: /dev/sdg1 is busy - skipping
mdadm: /dev/sdf1 is busy - skipping
mdadm: /dev/sde1 is busy - skipping
mdadm: /dev/sdd1 is busy - skipping
mdadm: /dev/sdc1 is busy - skipping
mdadm: /dev/sdb1 is busy - skipping

```

---

### Post by Silicon Knight on 2013-03-03
Okay so I may have made some progress.  I decided to downgrade my mdadm version from the one that came w/ the latest Ubuntu to the one that came with ubuntu 8 when I setup this raid.  As it turns out when I ran madadm --examine --scan -v it actually found the proper order (or so I think) that my drives were created in.  I re-issued the create with assume-clean with that order and it assembled as always but I am now able to find backup superblocks.

I'm restoring the superblocks now (taking a really long time as my memory keeps getting flooded and I need to restart) but hopefully it will prove positive.

I'll update when I find out just encase anyone has this problem also.

---

### Post by darkod on 2013-03-03
The first command, I don't think you can expect a superblock on the actual mdadm device, only on the partitions (or disks) that are members. As I can see, it finds all of them except one and assembles successfully.

Is there an actual problem you are seeing?

Be careful what commands you run on it, because you can mess it up and it looks good as it is.

---

### Post by Silicon Knight on 2013-03-03
> **darkod said:**
> The first command, I don't think you can expect a superblock on the actual mdadm device, only on the partitions (or disks) that are members. As I can see, it finds all of them except one and assembles successfully.

Is there an actual problem you are seeing?

Be careful what commands you run on it, because you can mess it up and it looks good as it is.

Yup shows no superbock on /dev/md0 and cant find filesystem once it assembles.  Looks like its not able to pull up the drive components into a filesystem.  It was able to find backup superblocks however with e2fsck.

I'm not sure how mdadm pulls togeather drives to show a file system but what I do know is when I try I get whats under.  It does assemble fine however just cant mount.  I've tried to force and specify filesystem but that does not work (ext4).

# mount /dev/md0 /media/STORAGE
```

mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail or so

```

---

### Post by darkod on 2013-03-03
Did you try fsck on assembled but not mounted md0?
sudo fsck /dev/md0

It can't do fsck on mounted, so it shouldn't be. If you are lucky this is only a small problem in the filesystem and fsck will deal with it. Because on mdadm level it all looks good, look at the /proc/mdstat you posted earlier, it says you have the md0 raid6 device as active, with only one member missing which is OK for a raid6 device since it can keep on working with two members missing.

---

### Post by Silicon Knight on 2013-03-04
Yea the fschk thats running now is being done via /dev/md0.  It found superblocks and  "seems" to be recreating the inodes but its taking A LONG time lol.  I suppose i should expect this?  Its sucking up lots of swap space.  Had to add 500gb more.

Thoughts?  Should this work?  I can "see" a partition via test disk

---

### Post by darkod on 2013-03-05
It's up to you. I would try the fsck first. Testdisk is used when recovering missing partitions, your md0 is not missing. Only the filesystem seems to have issues.

Also, since /dev/md0 is not a partition in the real meaning of the term, I'm not sure how testdisk would react and which is the partition it "sees".

---

### Post by Silicon Knight on 2013-03-05
Yeah I'm gong to let fsck finish, its taking a real long time but I assume that going to happen since i have 10x1.5TB in Raid6.  I just recently looked through the contents of my test-drive.log file, here is what it shows:

```

Analyse Disk /dev/md0 - 11 TB / 10 TiB - CHS 2929195008 2 4
Current partition structure:


Partition sector doesn't have the endmark 0xAA55
Ask the user for vista mode
Allow partial last cylinder : No
search_vista_part: 0


search_part()
Disk /dev/md0 - 11 TB / 10 TiB - CHS 2929195008 2 4


recover_EXT2: s_block_group_nr=0/11178, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 366284288
recover_EXT2: part_size 2930274304
     Linux                  512   0  1 366284799   1  4 2930274304
     EXT4 Large file Sparse superblock, 1500 GB / 1397 GiB

```

So I'm guessing I have 91,570,176 inodes (8192 inodes per group and 11178 groups) and I'm on inode 15,461,547.  So going to take a while LOL.

Oh Also I didn't "write" anything with test disk just using it in read mode basically to see whats on there via analyses.

---

