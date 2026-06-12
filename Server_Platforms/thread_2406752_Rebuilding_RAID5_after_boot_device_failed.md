---
title: "Rebuilding RAID5 after boot device failed"
date: 2018-11-25
forum: Server Platforms
---

### Post by simonwolton on 2018-11-25
After a power cut, my USB boot device fried. I think the array is still intact as mdadm shows the array as clean

[B]sudo mdadm --examine /dev/sd*

[/B]```

/dev/sda:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 274239f8:256036ee:804b2a17:b2a78367
           Name : nasbox:0  (local to host nasbox)
  Creation Time : Sun Oct  8 08:50:23 2017
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 7813771264 (3725.90 GiB 4000.65 GB)
     Array Size : 11720656896 (11177.69 GiB 12001.95 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : 06f9f725:33d00484:e7b01d19:0cc71589


Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Feb 12 23:31:06 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 44ce8971 - correct
         Events : 10435


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 274239f8:256036ee:804b2a17:b2a78367
           Name : nasbox:0  (local to host nasbox)
  Creation Time : Sun Oct  8 08:50:23 2017
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 7813771264 (3725.90 GiB 4000.65 GB)
     Array Size : 11720656896 (11177.69 GiB 12001.95 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : e3a8afa2:17c020f5:0fc2b704:e8439137


Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Feb 12 23:31:06 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : ccb7b74f - correct
         Events : 10435


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 1
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc:
   MBR Magic : aa55
Partition[0] :      7997440 sectors at         2048 (type 82)
Partition[1] :    112123906 sectors at      8001534 (type 05)
mdadm: No md superblock detected on /dev/sdc1.
/dev/sdc2:
   MBR Magic : aa55
Partition[0] :    112123904 sectors at            2 (type 83)
mdadm: No md superblock detected on /dev/sdc5.
/dev/sdd:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 274239f8:256036ee:804b2a17:b2a78367
           Name : nasbox:0  (local to host nasbox)
  Creation Time : Sun Oct  8 08:50:23 2017
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 7813771264 (3725.90 GiB 4000.65 GB)
     Array Size : 11720656896 (11177.69 GiB 12001.95 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : 842e88f9:c0204a64:66dfa2a8:bd349b1d


Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Feb 12 23:31:06 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 1caeabaf - correct
         Events : 10435


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sde:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 274239f8:256036ee:804b2a17:b2a78367
           Name : nasbox:0  (local to host nasbox)
  Creation Time : Sun Oct  8 08:50:23 2017
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 7813771264 (3725.90 GiB 4000.65 GB)
     Array Size : 11720656896 (11177.69 GiB 12001.95 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : f9e22c7f:4d6df5d0:f06377dd:6eb512d9


Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Feb 12 23:31:06 2018
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : ff4ab1ed - correct
         Events : 10435


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)

```

**sdc **is my boot drive, all others are identical 4TB drives.

When mounting however with mount /dev/md0 /mnt/raid, I get 

```
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error

```

**syslog **shows nothing, nor does **dmesg**
The array is made from 4TB disks so is GPT.

output of /proc/mdstat:

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sde1[3] sdd1[2] sdb1[1] sda1[0]
      11720656896 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      bitmap: 0/30 pages [0KB], 65536KB chunk


unused devices: <none>


```

I thought I'd end up rebuilding the raid array, but it seems clean. Is there a step or option I'm missing in order to mount the array?

Thanks

---

### Post by slickymaster on 2018-11-25
Thread moved to **Server Platforms** for a better fit

---

### Post by darkod on 2018-11-25
What filesystem did you have on the array?

It looks assembled good. I notice the chunk size is 512K. I assume it was like that before too.

If you re-assemble the array with the wrong device order or wrong chunk size, it will not be able to find the filesystem correctly so it won't mount. Even though it now looks like assembled clean, you need to make sure device order, chunk size and metadata version is same as it was before.

After that it should mount correctly when using the correct FS type.

---

