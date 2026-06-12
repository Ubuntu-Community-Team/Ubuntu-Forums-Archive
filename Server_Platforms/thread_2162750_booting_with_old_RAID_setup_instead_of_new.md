---
title: "booting with old RAID setup instead of new"
date: 2013-07-15
forum: Server Platforms
---

### Post by noumenon on 2013-07-15
I've been running into weird trouble with my raid array and I'm finally going to break down and ask for some help.  I'm running ubuntu server 13.04. 

I previously had two RAID 1 arrays set as md1 and md2.  md1 was two 2tb discs and md2 was two 3tb discs.  I then recently purchased four new 3tb discs and created a raid6 array.  I've copied all the data over, and then I broke down the old RAID arrays in order to cannabilize the discs for the new one.  I'm now trying to set up a RAID6 array with six 3tb discs at md0 (and I still have a 2tb RAID1 array at md1).  

Here is the problem: each time i boot it starts up md0, md1, and md2.  md0 only has 4 discs (instead of 6) and md1 and md2 are the original setups from the old arrays.  I then:
```
umount /media/Argus_Array
mdadm -S /dev/md0
mdadm -S /dev/md1
mdadm -S /dev/md2
mdadm --assemble --scan
```
Everything stops as expected and then this starts up md0 and md1 (but no md2 thankfully).  md0 however only has the 4 new discs and the old discs (which were part of md2 previously) are not part of the array. 
```
mdadm --detail 
```
returns two drives as removed.  I then manually add them back with
```
mdadm --add /dev/sd[bc]1
```
and they resync and everything seems to be fine... until I reboot and it starts all over. 

my mdadm.conf file:
```
DEVICE partitions
HOMEHOST Cmdr-Data
ARRAY /dev/md0 UUID=bad1a479:9429bfdd:32962bf4:44eb4136
ARRAY /dev/md1 UUID=f3415768:8a4aa943:b2d99281:ae8b99bd

```
(these are the correct UUIDs according to mdadm --detail)

I've also run ```
update-initramfs -u
```
and
```
update-initramfs -c -k all
```
several times, but this doesn't seem to have helped.  


not sure if it makes any difference, but I also can't get the computer to boot without it throwing up an error about the RAID being degraded (interestingly it gives an error about md1 and not md0).  I have ```
boot-degraded=true
``` set, but it doesn't seem to matter. 


any help would be much appreciated. 
Thanks,
noumenon

---

### Post by rubylaser on 2013-07-15
Can we see these?
```

mdadm --detail /dev/md0
mdadm --detail /dev/md1
mdadm --detail /dev/md2

```
and the metadata on each disk?
```

mdadm -E /dev/sd[X]1 #disks and partitions numbers for md1/2
mdadm -E /dev/sd[bcdefg]1 #guess at RAID6 partitions, replace with real values

```

---

### Post by noumenon on 2013-07-15
the array is currently resyncing, so I've already shut everything down and reassembled. As a result md2 no longer exists. 

md0
```
sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Fri Jul 12 20:07:34 2013
     Raid Level : raid6
     Array Size : 11720534016 (11177.57 GiB 12001.83 GB)
  Used Dev Size : 2930133504 (2794.39 GiB 3000.46 GB)
   Raid Devices : 6
  Total Devices : 6
    Persistence : Superblock is persistent

    Update Time : Mon Jul 15 20:15:08 2013
          State : clean, degraded, recovering
 Active Devices : 4
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 2

         Layout : left-symmetric
     Chunk Size : 512K

 Rebuild Status : 32% complete

           Name : Cmdr-Data:0  (local to host Cmdr-Data)
           UUID : bad1a479:9429bfdd:32962bf4:44eb4136
         Events : 11200

    Number   Major   Minor   RaidDevice State
       0       8       81        0      active sync   /dev/sdf1
       1       8       97        1      active sync   /dev/sdg1
       2       8      113        2      active sync   /dev/sdh1
       3       8      129        3      active sync   /dev/sdi1
       7       8       33        4      spare rebuilding   /dev/sdc1
       6       8       17        5      spare rebuilding   /dev/sdb1

```
prior to me manually adding sdc1 and sdb1 it simply said "removed" in the column where it now says "spare rebuilding".  It was not marked as a spare or anything. 


md1
```
sudo mdadm --detail /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Sat Jul 13 23:42:14 2013
     Raid Level : raid1
     Array Size : 1953382208 (1862.89 GiB 2000.26 GB)
  Used Dev Size : 1953382208 (1862.89 GiB 2000.26 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Mon Jul 15 20:19:20 2013
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : fileserver:1
           UUID : f3415768:8a4aa943:b2d99281:ae8b99bd
         Events : 147

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       8       65        1      active sync   /dev/sde1

```

md2, which should no longer exist... and doesn't appear to:
```
sudo mdadm --detail /dev/md2
mdadm: cannot open /dev/md2: No such file or directory

```

metadata on raid6 array (md0)
```
sudo mdadm -E /dev/sd[bcfghi]1 
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x2
     Array UUID : bad1a479:9429bfdd:32962bf4:44eb4136
           Name : Cmdr-Data:0  (local to host Cmdr-Data)
  Creation Time : Fri Jul 12 20:07:34 2013
     Raid Level : raid6
   Raid Devices : 6

 Avail Dev Size : 5860268032 (2794.39 GiB 3000.46 GB)
     Array Size : 11720534016 (11177.57 GiB 12001.83 GB)
  Used Dev Size : 5860267008 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
Recovery Offset : 1906088224 sectors
          State : clean
    Device UUID : 1851ddef:f7ded8f9:c2bc7c03:753d7826

    Update Time : Mon Jul 15 20:20:08 2013
       Checksum : 6a90673a - correct
         Events : 11203

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 5
   Array State : AAAAAA ('A' == active, '.' == missing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x2
     Array UUID : bad1a479:9429bfdd:32962bf4:44eb4136
           Name : Cmdr-Data:0  (local to host Cmdr-Data)
  Creation Time : Fri Jul 12 20:07:34 2013
     Raid Level : raid6
   Raid Devices : 6

 Avail Dev Size : 5860268032 (2794.39 GiB 3000.46 GB)
     Array Size : 11720534016 (11177.57 GiB 12001.83 GB)
  Used Dev Size : 5860267008 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
Recovery Offset : 1906088224 sectors
          State : clean
    Device UUID : c38cca08:798db7e0:1d4a0865:38b5d3ca

    Update Time : Mon Jul 15 20:20:08 2013
       Checksum : 70435686 - correct
         Events : 11203

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 4
   Array State : AAAAAA ('A' == active, '.' == missing)
/dev/sdf1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : bad1a479:9429bfdd:32962bf4:44eb4136
           Name : Cmdr-Data:0  (local to host Cmdr-Data)
  Creation Time : Fri Jul 12 20:07:34 2013
     Raid Level : raid6
   Raid Devices : 6

 Avail Dev Size : 5860268032 (2794.39 GiB 3000.46 GB)
     Array Size : 11720534016 (11177.57 GiB 12001.83 GB)
  Used Dev Size : 5860267008 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : e156a0c7:7c669a60:da68e5e4:8a2d655c

    Update Time : Mon Jul 15 20:20:08 2013
       Checksum : 4ecdf78d - correct
         Events : 11203

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAAAAA ('A' == active, '.' == missing)
/dev/sdg1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : bad1a479:9429bfdd:32962bf4:44eb4136
           Name : Cmdr-Data:0  (local to host Cmdr-Data)
  Creation Time : Fri Jul 12 20:07:34 2013
     Raid Level : raid6
   Raid Devices : 6

 Avail Dev Size : 5860268032 (2794.39 GiB 3000.46 GB)
     Array Size : 11720534016 (11177.57 GiB 12001.83 GB)
  Used Dev Size : 5860267008 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : e628f66f:29284c3e:dee8f67a:a682776a

    Update Time : Mon Jul 15 20:20:08 2013
       Checksum : 78f9605f - correct
         Events : 11203

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AAAAAA ('A' == active, '.' == missing)
/dev/sdh1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : bad1a479:9429bfdd:32962bf4:44eb4136
           Name : Cmdr-Data:0  (local to host Cmdr-Data)
  Creation Time : Fri Jul 12 20:07:34 2013
     Raid Level : raid6
Raid Devices : 6

 Avail Dev Size : 5860268032 (2794.39 GiB 3000.46 GB)
     Array Size : 11720534016 (11177.57 GiB 12001.83 GB)
  Used Dev Size : 5860267008 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : eaf3e27a:2c99d91f:74dd786f:e3eccd88

    Update Time : Mon Jul 15 20:20:08 2013
       Checksum : 784bfb3a - correct
         Events : 11203

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAAAAA ('A' == active, '.' == missing)
/dev/sdi1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : bad1a479:9429bfdd:32962bf4:44eb4136
           Name : Cmdr-Data:0  (local to host Cmdr-Data)
  Creation Time : Fri Jul 12 20:07:34 2013
     Raid Level : raid6
   Raid Devices : 6

 Avail Dev Size : 5860268032 (2794.39 GiB 3000.46 GB)
     Array Size : 11720534016 (11177.57 GiB 12001.83 GB)
  Used Dev Size : 5860267008 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 3d4ecba2:8d66f5d7:ab16cbc0:f89795a0

    Update Time : Mon Jul 15 20:20:08 2013
       Checksum : c16a073c - correct
         Events : 11203

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : AAAAAA ('A' == active, '.' == missing)


```


metadata on raid 1 array (md1)
```
sudo mdadm -E /dev/sd[de]1
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : f3415768:8a4aa943:b2d99281:ae8b99bd
           Name : fileserver:1
  Creation Time : Sat Jul 13 23:42:14 2013
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
     Array Size : 1953382208 (1862.89 GiB 2000.26 GB)
  Used Dev Size : 3906764416 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 6b922429:00fa4d17:6f2fdbd8:0e8a52e5

    Update Time : Mon Jul 15 20:19:34 2013
       Checksum : 15577713 - correct
         Events : 147


   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing)
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : f3415768:8a4aa943:b2d99281:ae8b99bd
           Name : fileserver:1
  Creation Time : Sat Jul 13 23:42:14 2013
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
     Array Size : 1953382208 (1862.89 GiB 2000.26 GB)
  Used Dev Size : 3906764416 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : fc0615a6:21a3a7cc:1010a88f:ccf4ddab

    Update Time : Mon Jul 15 20:19:34 2013
       Checksum : c4f9e025 - correct
         Events : 147


   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing)

```


also, here is the cat /proc/mdstat from prior to me shutting everything down. This is the old setup, with the addition of md0 and the four new discs:

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid6 sdf1[0] sdi1[3] sdh1[2] sdg1[1]
      11720534016 blocks super 1.2 level 6, 512k chunk, algorithm 2 [6/4] [UUUU__]

md2 : active raid1 sde[0] sdd[1]
      1953514496 blocks [2/2] [UU]

md1 : active raid1 sdb[1] sdc[0]
      2930265472 blocks [2/2] [UU]

unused devices: <none>
```


Thanks for you help,
noumenon

---

### Post by grunge09 on 2013-07-16
I ran into a similar problem with setting up 12.04 Server with 3x2tb drives in Raid 5.  I messed up the 1st time and re-installed the Server OS and the raid, but the install could not find any drives as I later found out they still had metadata on them.  I had tried to go back into the install and remove the detected raid setup there but no luck.  I had to boot off a GpartD CD and manually wipe each drive.  That got the metadata off of them.  Then I was able to re-install the Server OS and do the raid5 mdadm setup without a hitch.

To the wise ones who are smarter than me... Should he do this below?

So perhaps it is still seeing the old metadata from the old RAID1 2x3tb on the HD's.  Try wiping those 2 discs only.  I would disconnect that whole raid6 and raid1 and hook up just those 2 drives you cannibalised and use gparted to wipe the metadata and partitions off the 2 affected drives.  See if that helps?

---

### Post by noumenon on 2013-07-16
That's a bingo!

Don't sell yourself short.  I ran 

mdadm --examine --verbose --scan

and both sets of array data were present.  I took down both arrays and zeroed the superblocks on all the old drives.  Reassembled and resynced and now it works like a champ. 

after doing all this, running
mdadm --examine --verbose --scan
returns:
```
ARRAY /dev/md/1 level=raid1 metadata=1.2 num-devices=2 UUID=f3415768:8a4aa943:b2d99281:ae8b99bd name=fileserver:1
   devices=/dev/sdd1,/dev/sde1
ARRAY /dev/md/0 level=raid6 metadata=1.2 num-devices=6 UUID=bad1a479:9429bfdd:32962bf4:44eb4136 name=Cmdr-Data:0
   devices=/dev/sdi1,/dev/sdh1,/dev/sdg1,/dev/sdf1,/dev/sdb1,/dev/sdc1
```
just like it should.


Thanks a bunch, 
noumenon


marked as solved.

---

