---
title: "RAID drives suddenly become spare drives"
date: 2012-11-16
forum: Server Platforms
---

### Post by _dolittle_ on 2012-11-16
Hi,
i have a serious raid problem here. I'm running here a RAID-5/LVM configuration consisting of 3 physical harddrives of 2TB each. Each drive has 8 partitions of about 250gigs. Only the last partition has less because 2TB/8 is less than 250gig which is compensated here.

**RAID**
The first 7 sets of partitions (sdaX,sdbX and sdcX) is configured as a RAID5 providing 500gigs per set. The 8th set is configured as a RAID1 for fault tolerance.

**LVM**
The LVM configuration combines the 7 raids to one logical volume.

I chose this setup to minimize the recovery time if one raid set has problems and needs recovery.

The system is a Lucid (10.4 LTS) server installation.

**Here's my problem**

For some time one drive is behaving a little bit strange and is failing sometimes on startup of the system. A restart fixed it until now. Sometimes this means that the raid has to regenerate some sets or the whole raid. Yesterdays fail caused a full regeneration over all 7 raids.
Usually this takes one night and the system is back again.

The output of more /proc/mdstat is something like this
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sda8[0] sdc8[1] sdb8[3]
116390840 blocks super 1.2 [3/2] [_UU]
resync=DELAYED

md1 : active raid5 sda1[0] sdc1[1] sdb1[3]
524285568 blocks super 1.2 level 5, 64k chunk, algorithm 2 [3/2] [_UU]
resync=DELAYED

md7 : active raid5 sda7[4] sdc7[1] sdb7[3]
524285568 blocks super 1.2 level 5, 64k chunk, algorithm 2 [3/2] [_UU]
resync=DELAYED

md6 : active raid5 sda6[0] sdc6[1] sdb6[3]
524285568 blocks super 1.2 level 5, 64k chunk, algorithm 2 [3/2] [_UU]
[>....................] recovery = 0.0% (85120/262142784) finish=564.3min speed=7738K/sec

md5 : active raid5 sda5[0] sdc5[1] sdb5[3]
524285568 blocks super 1.2 level 5, 64k chunk, algorithm 2 [3/2] [_UU]
resync=DELAYED

md4 : active raid5 sda4[0] sdc4[1] sdb4[3]
524285568 blocks super 1.2 level 5, 64k chunk, algorithm 2 [3/2] [_UU]
resync=DELAYED

md3 : active raid5 sda3[4] sdc3[1] sdb3[3]
524285568 blocks super 1.2 level 5, 64k chunk, algorithm 2 [3/2] [_UU]
resync=DELAYED

md2 : active raid5 sda2[0] sdc2[4] sdb2[3]
524285568 blocks super 1.2 level 5, 64k chunk, algorithm 2 [3/2] [_UU]
resync=DELAYED
```

But suddenly in the morning some partitions of healthy parts of some raids became spare drives. As a result the /proc/mdadm looks now like this
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sda8[0] sdc8[1](F) sdb8[3]
      116390840 blocks super 1.2 [3/2] [U_U]

md1 : active raid5 sda1[0](S) sdc1[1](F) sdb1[3]
      524285568 blocks super 1.2 level 5, 64k chunk, algorithm 2 [3/1] [__U]

md7 : active raid5 sda7[4] sdc7[1](F) sdb7[3]
      524285568 blocks super 1.2 level 5, 64k chunk, algorithm 2 [3/2] [U_U]

md6 : active raid5 sda6[0] sdc6[1](F) sdb6[3]
      524285568 blocks super 1.2 level 5, 64k chunk, algorithm 2 [3/2] [U_U]

md5 : active raid5 sda5[0](S) sdc5[1](F) sdb5[3]
      524285568 blocks super 1.2 level 5, 64k chunk, algorithm 2 [3/1] [__U]

md4 : active raid5 sda4[0](S) sdc4[1](F) sdb4[3]
      524285568 blocks super 1.2 level 5, 64k chunk, algorithm 2 [3/1] [__U]

md3 : active raid5 sda3[4] sdc3[1](F) sdb3[3]
      524285568 blocks super 1.2 level 5, 64k chunk, algorithm 2 [3/2] [U_U]

md2 : active raid5 sda2[0] sdc2[4](F) sdb2[3]
      524285568 blocks super 1.2 level 5, 64k chunk, algorithm 2 [3/2] [U_U]

unused devices: <none>

```

To fix the failed drive sdc the system had to be rebooted but i don't know how to deal with the "sudden" spares. Therefore i don't dare to do the reboot now.

_Can please someone help me and provide ideas what to do?_

Thanks very much in advance

dolittle

---

### Post by _dolittle_ on 2012-11-16
Does nobody have an idea?

Please help me. This is really bad for me.

Thanks in advance

dolittle

---

### Post by darkod on 2012-11-16
I'm not mdadm expert, and I understand you want to know ASAP how to fix this, but you will have to be patient someone to jump in.

Meanwhile, you can get more details about md1 for example, which has one spare and one failed partition with:
sudo mdadm -E /dev/sd[abc]1

That will list mdadm superblock details for all three partitions. I would watch out for the Events counter. They should match on all partitions, or at least on two.

You can start with posting those details.

---

### Post by _dolittle_ on 2012-11-16
Thanks for the reply. Drive sdc is completely offline right now. But it will be up again after the next boot. I don't worry about it. It will have to be replaced but thats a different story. 

Due to this i can post only for sdaX and sdbX

mdadm -E output for md1
```
root@mediacenter:~# mdadm -E /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : b62960c9:9c2ff240:6ce247d2:89823d8a
           Name : ubuntu:1
  Creation Time : Wed Jun 22 00:36:45 2011
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 524285952 (250.00 GiB 268.43 GB)
     Array Size : 1048571136 (500.00 GiB 536.87 GB)
  Used Dev Size : 524285568 (250.00 GiB 268.43 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 67c323c2:ebe508d2:24c05758:0b0dc597

    Update Time : Fri Nov 16 13:09:14 2012
       Checksum : 1067e5d2 - correct
         Events : 18532

         Layout : left-symmetric
     Chunk Size : 64K

    Array Slot : 0 (empty, failed, failed, 2, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed)
   Array State : __u 382 failed
root@mediacenter:~# mdadm -E /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : b62960c9:9c2ff240:6ce247d2:89823d8a
           Name : ubuntu:1
  Creation Time : Wed Jun 22 00:36:45 2011
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 524287728 (250.00 GiB 268.44 GB)
     Array Size : 1048571136 (500.00 GiB 536.87 GB)
  Used Dev Size : 524285568 (250.00 GiB 268.43 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : ee43ca75:0e6d9d6e:970e905c:e94053a9

    Update Time : Fri Nov 16 13:09:14 2012
       Checksum : 76696fcf - correct
         Events : 18532

         Layout : left-symmetric
     Chunk Size : 64K

    Array Slot : 3 (empty, failed, failed, 2, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed)
   Array State : __U 382 failed

```

mdadm -E output for md4
```
root@mediacenter:~# mdadm -E /dev/sda4
/dev/sda4:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 6cace689:3fa697ee:d1d9b0fd:a9f13de2
           Name : ubuntu:4
  Creation Time : Wed Jun 22 00:37:35 2011
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 524285952 (250.00 GiB 268.43 GB)
     Array Size : 1048571136 (500.00 GiB 536.87 GB)
  Used Dev Size : 524285568 (250.00 GiB 268.43 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 24f7210c:a33ddc95:f30cc951:393be419

    Update Time : Fri Nov 16 05:43:48 2012
       Checksum : 8e5f394f - correct
         Events : 40390

         Layout : left-symmetric
     Chunk Size : 64K

    Array Slot : 0 (empty, failed, failed, 2, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed)
   Array State : __u 382 failed
root@mediacenter:~# mdadm -E /dev/sdb4
/dev/sdb4:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 6cace689:3fa697ee:d1d9b0fd:a9f13de2
           Name : ubuntu:4
  Creation Time : Wed Jun 22 00:37:35 2011
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 524287728 (250.00 GiB 268.44 GB)
     Array Size : 1048571136 (500.00 GiB 536.87 GB)
  Used Dev Size : 524285568 (250.00 GiB 268.43 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : aa86866e:ad5cb9e0:b30b61ea:2d18bde6

    Update Time : Fri Nov 16 05:43:48 2012
       Checksum : a111c398 - correct
         Events : 40390

         Layout : left-symmetric
     Chunk Size : 64K

    Array Slot : 3 (empty, failed, failed, 2, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed)
   Array State : __U 382 failed

```

mdadm -E output for md5
```

root@mediacenter:~# mdadm -E /dev/sda5
/dev/sda5:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 99891c18:4900aaee:7c7d140a:9e965a91
           Name : ubuntu:5
  Creation Time : Wed Jun 22 00:37:45 2011
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 524285952 (250.00 GiB 268.43 GB)
     Array Size : 1048571136 (500.00 GiB 536.87 GB)
  Used Dev Size : 524285568 (250.00 GiB 268.43 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 1ab1ee6a:bfb2e8cd:3f8df469:e7164bae

    Update Time : Fri Nov 16 05:43:48 2012
       Checksum : 1c959d48 - correct
         Events : 194258

         Layout : left-symmetric
     Chunk Size : 64K

    Array Slot : 0 (empty, failed, failed, 2, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed)
   Array State : __u 382 failed
root@mediacenter:~# mdadm -E /dev/sdb5
/dev/sdb5:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 99891c18:4900aaee:7c7d140a:9e965a91
           Name : ubuntu:5
  Creation Time : Wed Jun 22 00:37:45 2011
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 524287728 (250.00 GiB 268.44 GB)
     Array Size : 1048571136 (500.00 GiB 536.87 GB)
  Used Dev Size : 524285568 (250.00 GiB 268.43 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : f6c5ea70:78ce33ae:55cdb935:ed4fc916

    Update Time : Fri Nov 16 05:43:48 2012
       Checksum : 372046fb - correct
         Events : 194258

         Layout : left-symmetric
     Chunk Size : 64K

    Array Slot : 3 (empty, failed, failed, 2, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed)
   Array State : __U 382 failed

```

The events counters match on each pair. I hope there's an easy way just to "switch" the Spare partitions back to normal, reboot and wait for the rebuild.

Hope someone has an idea.

Thanks

---

### Post by madverb on 2012-11-16
Don't use RAID5 ever.

---

### Post by darkod on 2012-11-16
The events counters give some hope, but since this is a raid5 array and one disk was already failing, I am worried is it still good with partitions from a second disk marked as spare.

I'll try to contact one guy that knows much more about mdadm, but lets see if he can join the discussion.

PS. This is probably not what you want to hear, but with one disk failing regularly you decided to keep running a raid5 array which tolerates only one disk failure. You were asking for trouble if something happens to a second disk, and it finally did.

---

### Post by _dolittle_ on 2012-11-16
Thanks. You're very nice.

---

### Post by rubylaser on 2012-11-16
Well, this is the most convoluted mdadm setup I've ever seen. This is just asking for breakage, and I'm honestly surprised it's worked well for you for some time.  First question, do you have a backup of this data? 

The first step to try to remedy this is to reboot, and get /dev/sdc online.  The next step is to run smartmontools on each disk and verify their health.

```
apt-get install smartmontools
smartctl -a /dev/sda
smartctl -a /dev/sdb
smartctl -a /dev/sdc
```

If all disks pass and SMART test, and don't have a bunch of Reallocated or Pending Sectors, then you can continue, if not, post back for further instructions.

You are going to need to force assemble the arrays, that have disks marked as spares to get them back online.
```
mdadm --assemble --force /dev/md1 /dev/sd[abc]1
mdadm --assemble --force /dev/md4 /dev/sd[abc]4
```

If you can get this restored, I'd really suggest rebuilding / reconfiguring your arrays to greatly simplify this, and to add another disk and migrate to a RAID6.

---

### Post by CharlesA on 2012-11-16
@OP: I have never seen a RAID 5 set up like that.

> **madverb said:**
> Don't use RAID5 ever.
Got a reason for that?

Oh yeah, +1 to Ruby - he is very good with mdadm. ;)

---

### Post by _dolittle_ on 2012-11-17
@rubylaser: Thanks for the information. I'll report back as soon as I'm finished. It may take some hours since I try to salvage everthing readable from the raid.

> **CharlesA said:**
> @OP: I have never seen a RAID 5 set up like that.


Some of you seen to have ideas for improvement of my raid setup I'd be happy if you'd share them with me. It would be a perfect time to execute them.

Thanks for your help

---

### Post by rubylaser on 2012-11-17
> **_dolittle_ said:**
> @rubylaser: Thanks for the information. I'll report back as soon as I'm finished. It may take some hours since I try to salvage everthing readable from the raid.



Some of you seen to have ideas for improvement of my raid setup I'd be happy if you'd share them with me. It would be a perfect time to execute them.

Thanks for your help

I would love to know what you use your array for (i.e. pictures, videos, documents, backups, VM storage, etc.)  This would make recommending a RAID setup much easier.

---

### Post by CharlesA on 2012-11-17
> **_dolittle_ said:**
> 
Some of you seen to have ideas for improvement of my raid setup I'd be happy if you'd share them with me. It would be a perfect time to execute them.

Thanks for your help

I would need to know what you intent to use the array for, but off the top of my head, I would suggest going with RAID 6 because you have so many drives - but that is only from a data storage standpoint.

> **rubylaser said:**
> I would love to know what you use your array for (i.e. pictures, videos, documents, backups, VM storage, etc.)  This would make recommending a RAID setup much easier.

Agreed. I use my array (RAID5) for backups, file storage, VM storage.. and all that, but RAID isn't a "one size fits all" type of thing.

---

### Post by _dolittle_ on 2012-11-17
Thanks to you my situation seems to improve.

Current situation: All drives are up and running

Raid assembling worked on the second try. Had to stop and assemble two of the arrays to get them up.

mdstat ist looking like this
```
root@mediacenter:/home/ludwig# more /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid5 sdd1[1] sdb1[0] sdc1[3]
      524285568 blocks super 1.2 level 5, 64k chunk, algorithm 2 [3/2] [_UU]
        resync=DELAYED

md0 : active raid1 sdd8[1] sdc8[3] sdb8[0]
      116390840 blocks super 1.2 [3/2] [U_U]
        resync=DELAYED

md7 : active raid5 sdd7[1] sdc7[3] sdb7[4]
      524285568 blocks super 1.2 level 5, 64k chunk, algorithm 2 [3/2] [U_U]
      [>....................]  recovery =  2.1% (5739036/262142784) finish=103.3min speed=41349K/sec

md6 : active raid5 sdd6[1] sdc6[3] sdb6[0]
      524285568 blocks super 1.2 level 5, 64k chunk, algorithm 2 [3/2] [U_U]
        resync=DELAYED

md5 : active raid5 sdd5[1] sdc5[3] sdb5[0]
      524285568 blocks super 1.2 level 5, 64k chunk, algorithm 2 [3/2] [_UU]
        resync=DELAYED

md4 : active raid5 sdd4[1] sdb4[0] sdc4[3]
      524285568 blocks super 1.2 level 5, 64k chunk, algorithm 2 [3/2] [_UU]
        resync=DELAYED

md3 : active raid5 sdd3[1] sdc3[3] sdb3[4]
      524285568 blocks super 1.2 level 5, 64k chunk, algorithm 2 [3/2] [U_U]
        resync=DELAYED

md2 : active raid5 sdd2[4] sdc2[3] sdb2[0]
      524285568 blocks super 1.2 level 5, 64k chunk, algorithm 2 [3/2] [U_U]
        resync=DELAYED

unused devices: <none>

```

I keep my fingers crossed that this is going to work.

And thanks again for your help

---

### Post by _dolittle_ on 2012-11-17
> **rubylaser said:**
> I would love to know what you use your array for (i.e. pictures, videos, documents, backups, VM storage, etc.)  This would make recommending a RAID setup much easier.

The main usage for the system is a file server for media files like music, video, etc. It also has a TV card for recording purposes. So the majority of the files are quite large.

There's also the mirror set that contains very important document files shared in the internal network and automatically backed up in the cloud.

There are also some other services like a web server or subversion but they are used not much compared to samba.

Since it is likely to happen to run out of space one goal would be easy extensability. But currently I have only 4 SATA ports.

Does this provide a picture sufficient for a proposal?

Thanks

dolittle

---

### Post by rubylaser on 2012-11-17
I love mdadm and use it everyday, but for home media storage, I've personally switched over to [Snapraid]("http://snapraid.sourceforge.net/").  Each disk is independent and is mounted like a normal ext4 filesystem.  This means that even if you lose more parity than your array supports, you still only lose the data on that one disk. 

I have a tutorials for both mdadm or snapraid in my signature if you are interested.  Either way, Snapraid or mdadm, I'd use RAID6, and use one big array, no need for a bunch of little arrays, or even LVM.  You can expand either one of these solutions without the need for LVM.

If you have an extra PCI-Express x8 or x16 slot, you can easily add a card like the [IBM m1015]("http://www.ebay.com/sch/i.html?_trksid=p5197.m570.l1313&_nkw=ibm+m1015&_sacat=0&_from=R40") or [BR10i ]("http://www.ebay.com/sch/i.html?_odkw=ibm+m1015&_osacat=0&_from=R40&_trksid=p2045573.m570.l1313&_nkw=ibm+br10i&_sacat=0") flashed to IT mode and add up to 8 SATA ports (you'll need [forward breakout cables]("http://www.monoprice.com/products/subdepartment.asp?c_id=102&cp_id=10254&cs_id=1025406") for either of these to hook up to disks).

---

### Post by CharlesA on 2012-11-17
I haven't used Snapraid at all, but I do +1 using RAID6 with that number of disks.

I've been running RAID5 with 3 drives, but anything with 5 or more would be better off running RAID6.

---

