---
title: "RAID5 won't reassemble even when all disks have same UUID"
date: 2009-09-03
forum: Server Platforms
---

### Post by mbhkewl on 2009-09-03
History:
I have a RAID5 array of 8 disks, each 1TB. 7 disks used & 1 spare. Everything was working fine, until I decided to expand the storage to that spare.

While it was reshaping/growing, something weird happened and kicked out 2 disks! The spare remained inside but 2 other disks which were sane are now out.

```
md0 : active raid5 sdf1[8](F) sdd1[7] sdb1[6] sdh1[5] sda1[4] sdg1[9](F) sdc1[2] sde1[1]
12:56 PM  5860558848 blocks super 0.91 level 5, 256k chunk, algorithm 2 [8/6] [_UU_UUUU]
```mdadm -E /dev/sd[a-h]1
shows all data of all disks.

I was running Ubuntu Server 8.10: ```
Linux Adam 2.6.27-14-server #1 SMP Tue Aug 18 17:21:37 UTC 2009 i686 GNU/Linux
```After a reboot, the array would never come up. Assembling fails with: ```
mdadm: superblock on /dev/sda1 doesn't match others - assembly aborted
```It doesn't matter which disk is put first in the assemble command, mdadm complains that that disk doesn't match others. (Yes, I did try using the proper order).

After trying many things for a whole day (but never to recreate the array!), I decided to do a dist-upgrade to Ubuntu Server 9.04.
Now, I'm running the latest kernel: ```
Linux Adam 2.6.28-15-server #49-Ubuntu SMP Tue Aug 18 19:30:06 UTC 2009 i686 GNU/Linux
```Now I am able to see the array and all the disks (as spares):
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdd1[7](S) sde1[1](S) sda1[4](S) sdb1[6](S) sdf1[0](S) sdh1[5](S) sdc1[2](S) sdg1[3](S)
      7814078464 blocks super 0.91
```When I try to run mdadm: ```
root@Adam:~# mdadm -R --verbose /dev/md0
mdadm: failed to run array /dev/md0: Input/output error
root@Adam:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdd1[7] sde1[1] sda1[4] sdb1[6] sdh1[5] sdc1[2]
      5860558848 blocks super 0.91

unused devices: <none>
```Two disks are thrown out now. I try to reassemble the array:
```
root@Adam:~# mdadm --assemble --verbose /dev/md0 /dev/sdf1 /dev/sde1 /dev/sdc1 /dev/sdg1 /dev/sda1 /dev/sdh1 /dev/sdb1 /dev/sdd1
mdadm: looking for devices for /dev/md0
mdadm: superblock on /dev/sdf1 doesn't match others - assembly aborted
```The UUID of all the disks is the same and are found to be all part of the same array: ```
root@Adam:~# mdadm -Es /dev/sd[a-h]1
ARRAY /dev/md0 level=raid5 num-devices=8 UUID=ed1a2670:03308d80:95a69c9f:ccf9605f
```Attached is the full examine output of mdadm along with the disk brands and models.

I want the array to reassemble so that it could resume reshaping.

I should also mention that the filesystem is XFS, and before growing the array, it was mounted as read-only (I had a hunch something wrong was gonna happen...)

I appreciate all the help I can get on this. I had my share of problems with mdadm but I was always able to work it out. This is the first time I'm stumped :/

---

### Post by mbhkewl on 2009-09-05
I'm not sure if this is right, so correct me if I'm wrong:

The array stopped while reshaping/growing, if I create a new array, would the new array continue reshaping?

Or should I create a new array of 7 disks instead of 8 and exclude the disk that was a spare?

---

### Post by mbhkewl on 2009-09-10
After days of searching with no avail, I subscribed to the linux-raid mailing list and got help from there. You can find the message trail [in the archive here]("http://marc.info/?l=linux-raid&m=125223124630972&w=2").

I'll include some details and then the solution, but first I'd like to say something to Ubuntu Server maintenance team:

[B][SIZE=4][COLOR=Red]This is Canonical's fault!!![/COLOR] The packages in their repositories are old and have many bugs unfixed even though newer versions have been released!

If you're using mdadm, grab the latest version from the link below!
[/SIZE][/B]
_**Details:**_
I forgot to mention that I'm running mdadm 2.6.7.1 ([I]latest in Ubuntu
Server repositories[/I]).

I tried forcing the assembly, but as mentioned, I just got an error:
root@Adam:/var/www# mdadm -Af /dev/md0
mdadm: superblock on /dev/sdh1 doesn't match others - assembly aborted

I know I could've pasted whatever I wrote here, but it seemed
redundant. I'll keep your hint in mind for the next time, if any
(hopefully not).

This may be of an interest to you:
root@Adam:/var/www# mdadm -E /dev/sd[a-h]1 | grep Reshap
sda1  Reshape pos'n : 3357066496 (3201.55 GiB 3437.64 GB)
sdb1  Reshape pos'n : 3357066496 (3201.55 GiB 3437.64 GB)
sdc1  Reshape pos'n : 3357066496 (3201.55 GiB 3437.64 GB)
sdd1  Reshape pos'n : 3357066496 (3201.55 GiB 3437.64 GB)
sde1  Reshape pos'n : 3357066496 (3201.55 GiB 3437.64 GB)
sdf1   Reshape pos'n : 3357066496 (3201.55 GiB 3437.64 GB)
sdg1  Reshape pos'n : 2554257664 (2435.93 GiB 2615.56 GB)
sdh1  Reshape pos'n : 3357066496 (3201.55 GiB 3437.64 GB)

Note that sdd1 was the spare.

The UUIDs are all the same and the superblock is all similar except
for the reshaping position of sdg1.

I didn't try to recreate the array as I've never faced this issue
before, so I don't know what kind of repercussions it may have.
Here's the full output of mdadm --examine /dev/sd[a-h]1 (I'm including it so that it can be indexed by search engines)
Here's the output of examine:

/dev/sda1:
          Magic : a92b4efc
        Version : 00.91.00
           UUID : ed1a2670:03308d80:95a69c9f:ccf9605f
  Creation Time : Sat May 23 00:22:49 2009
     Raid Level : raid5
  Used Dev Size : 976759808 (931.51 GiB 1000.20 GB)
     Array Size : 6837318656 (6520.58 GiB 7001.41 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

  Reshape pos'n : 3357066496 (3201.55 GiB 3437.64 GB)
  Delta Devices : 1 (7->8)

    Update Time : Wed Sep  2 13:28:39 2009
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 5b5a1163 - correct
         Events : 949214

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     4       8        1        4      active sync   /dev/sda1

   0     0       0        0        0      removed
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       0        0        3      faulty removed
   4     4       8        1        4      active sync   /dev/sda1
   5     5       8      113        5      active sync   /dev/sdh1
   6     6       8       17        6      active sync   /dev/sdb1
   7     7       8       49        7      active sync   /dev/sdd1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.91.00
           UUID : ed1a2670:03308d80:95a69c9f:ccf9605f
  Creation Time : Sat May 23 00:22:49 2009
     Raid Level : raid5
  Used Dev Size : 976759808 (931.51 GiB 1000.20 GB)
     Array Size : 6837318656 (6520.58 GiB 7001.41 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

  Reshape pos'n : 3357066496 (3201.55 GiB 3437.64 GB)
  Delta Devices : 1 (7->8)

    Update Time : Wed Sep  2 13:28:39 2009
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 5b5a1177 - correct
         Events : 949214

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     6       8       17        6      active sync   /dev/sdb1

   0     0       0        0        0      removed
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       0        0        3      faulty removed
   4     4       8        1        4      active sync   /dev/sda1
   5     5       8      113        5      active sync   /dev/sdh1
   6     6       8       17        6      active sync   /dev/sdb1
   7     7       8       49        7      active sync   /dev/sdd1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.91.00
           UUID : ed1a2670:03308d80:95a69c9f:ccf9605f
  Creation Time : Sat May 23 00:22:49 2009
     Raid Level : raid5
  Used Dev Size : 976759808 (931.51 GiB 1000.20 GB)
     Array Size : 6837318656 (6520.58 GiB 7001.41 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

  Reshape pos'n : 3357066496 (3201.55 GiB 3437.64 GB)
  Delta Devices : 1 (7->8)

    Update Time : Wed Sep  2 13:28:39 2009
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 5b5a117f - correct
         Events : 949214

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     2       8       33        2      active sync   /dev/sdc1

   0     0       0        0        0      removed
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       0        0        3      faulty removed
   4     4       8        1        4      active sync   /dev/sda1
   5     5       8      113        5      active sync   /dev/sdh1
   6     6       8       17        6      active sync   /dev/sdb1
   7     7       8       49        7      active sync   /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.91.00
           UUID : ed1a2670:03308d80:95a69c9f:ccf9605f
  Creation Time : Sat May 23 00:22:49 2009
     Raid Level : raid5
  Used Dev Size : 976759808 (931.51 GiB 1000.20 GB)
     Array Size : 6837318656 (6520.58 GiB 7001.41 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

  Reshape pos'n : 3357066496 (3201.55 GiB 3437.64 GB)
  Delta Devices : 1 (7->8)

    Update Time : Wed Sep  2 13:28:39 2009
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 5b5a1199 - correct
         Events : 949214

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     7       8       49        7      active sync   /dev/sdd1

   0     0       0        0        0      removed
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       0        0        3      faulty removed
   4     4       8        1        4      active sync   /dev/sda1
   5     5       8      113        5      active sync   /dev/sdh1
   6     6       8       17        6      active sync   /dev/sdb1
   7     7       8       49        7      active sync   /dev/sdd1
/dev/sde1:
          Magic : a92b4efc
        Version : 00.91.00
           UUID : ed1a2670:03308d80:95a69c9f:ccf9605f
  Creation Time : Sat May 23 00:22:49 2009
     Raid Level : raid5
  Used Dev Size : 976759808 (931.51 GiB 1000.20 GB)
     Array Size : 6837318656 (6520.58 GiB 7001.41 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

  Reshape pos'n : 3357066496 (3201.55 GiB 3437.64 GB)
  Delta Devices : 1 (7->8)

    Update Time : Wed Sep  2 13:28:39 2009
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 5b5a119d - correct
         Events : 949214

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     1       8       65        1      active sync   /dev/sde1

   0     0       0        0        0      removed
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       0        0        3      faulty removed
   4     4       8        1        4      active sync   /dev/sda1
   5     5       8      113        5      active sync   /dev/sdh1
   6     6       8       17        6      active sync   /dev/sdb1
   7     7       8       49        7      active sync   /dev/sdd1
/dev/sdf1:
          Magic : a92b4efc
        Version : 00.91.00
           UUID : ed1a2670:03308d80:95a69c9f:ccf9605f
  Creation Time : Sat May 23 00:22:49 2009
     Raid Level : raid5
  Used Dev Size : 976759808 (931.51 GiB 1000.20 GB)
     Array Size : 6837318656 (6520.58 GiB 7001.41 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

  Reshape pos'n : 3357066496 (3201.55 GiB 3437.64 GB)
  Delta Devices : 1 (7->8)

    Update Time : Wed Sep  2 06:40:04 2009
          State : clean
 Active Devices : 7
Working Devices : 7
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 5b59b1c1 - correct
         Events : 949204

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     0       8       81        0      active sync   /dev/sdf1

   0     0       8       81        0      active sync   /dev/sdf1
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       0        0        3      faulty removed
   4     4       8        1        4      active sync   /dev/sda1
   5     5       8      113        5      active sync   /dev/sdh1
   6     6       8       17        6      active sync   /dev/sdb1
   7     7       8       49        7      active sync   /dev/sdd1
/dev/sdg1:
          Magic : a92b4efc
        Version : 00.91.00
           UUID : ed1a2670:03308d80:95a69c9f:ccf9605f
  Creation Time : Sat May 23 00:22:49 2009
     Raid Level : raid5
  Used Dev Size : 976759808 (931.51 GiB 1000.20 GB)
     Array Size : 6837318656 (6520.58 GiB 7001.41 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

  Reshape pos'n : 2554257664 (2435.93 GiB 2615.56 GB)
  Delta Devices : 1 (7->8)

    Update Time : Wed Sep  2 00:10:39 2009
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : fba3471a - correct
         Events : 874530

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     3       8       97        3      active sync   /dev/sdg1

   0     0       8       81        0      active sync   /dev/sdf1
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       97        3      active sync   /dev/sdg1
   4     4       8        1        4      active sync   /dev/sda1
   5     5       8      113        5      active sync   /dev/sdh1
   6     6       8       17        6      active sync   /dev/sdb1
   7     7       8       49        7      active sync   /dev/sdd1
/dev/sdh1:
          Magic : a92b4efc
        Version : 00.91.00
           UUID : ed1a2670:03308d80:95a69c9f:ccf9605f
  Creation Time : Sat May 23 00:22:49 2009
     Raid Level : raid5
  Used Dev Size : 976759808 (931.51 GiB 1000.20 GB)
     Array Size : 6837318656 (6520.58 GiB 7001.41 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

  Reshape pos'n : 3357066496 (3201.55 GiB 3437.64 GB)
  Delta Devices : 1 (7->8)

    Update Time : Wed Sep  2 13:28:39 2009
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 5b5a11d5 - correct
         Events : 949214

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     5       8      113        5      active sync   /dev/sdh1

   0     0       0        0        0      removed
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       0        0        3      faulty removed
   4     4       8        1        4      active sync   /dev/sda1
   5     5       8      113        5      active sync   /dev/sdh1
   6     6       8       17        6      active sync   /dev/sdb1
   7     7       8       49        7      active sync   /dev/sdd1


_**The Solution:**_Mr. Neil Brown had told me the following:
> You will need at least 2.6.8 to be able to assemble arrays which are
in the middle of a reshape.  I would suggest 2.6.9 or 3.0.> > root@Adam:/var/www# mdadm -Af /dev/md0
> mdadm: superblock on /dev/sdh1 doesn't match others - assembly aborted

This incorrect message is fixed in 2.6.8 an later.I [downloaded]("http://www.kernel.org/pub/linux/utils/raid/mdadm/") & compiled (quite easy for those of you who never tried it before) mdadm 3.0 and everything worked like charm!
To compile, just open a shell, go to the directory where you downloaded mdadm's comperessed file, unpack it, go inside the new directory and type: make, then sudo make install

Make sure you have uninstalled the old version of mdadm first!

This is the result after force assembling my broken array:
```
root@Adam:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5]
[raid4] [raid10]
md0 : active raid5 sdf1[[0]]("http://marc.info/?l=linux-raid&m=125228175505400&w=2#0") sdd1[[7]]("http://marc.info/?l=linux-raid&m=125228175505400&w=2#7") sdb1[[6]]("http://marc.info/?l=linux-raid&m=125228175505400&w=2#6") sdh1[[5]]("http://marc.info/?l=linux-raid&m=125228175505400&w=2#5") sda1[[4]]("http://marc.info/?l=linux-raid&m=125228175505400&w=2#4") sdc1[[2]]("http://marc.info/?l=linux-raid&m=125228175505400&w=2#2") sde1[[1]]("http://marc.info/?l=linux-raid&m=125228175505400&w=2#1")
      5860558848 blocks super 0.91 level 5, 256k chunk, algorithm 2
[8/7] [UUU_UUUU]
      [=========>...........]  reshape = 49.1% (479633152/976759808)
finish=950.5min speed=8704K/sec
```Notice that sdg1 is not part of the array anymore, and now the array is reshaping while degraded!
I have to wait until it finishes reshaping then add sdg1 (if it proves to be good) or put a new disk.

EDIT/Correction:
The whole thing happened because of some bloody cables, not the MSI motherboard that I have.
I've changed the cables and things seem to be stable now. (no more link errors & ata errors reported by dmesg).

---

### Post by fjgaude on 2009-09-10
Yes, it's hard to understand why mdadm 2.6.7 is current in 9.04 and not 2.6.8. It's also amazing you can recover without loss of data by using it, from the kind of thing you went through with your MB. In all the years of using mdadm I've not had to go through what you did. <smile>

I'll look to see what version is in 9.10 when Beta comes out.

---

### Post by mbhkewl on 2009-09-10
> **fjgaude said:**
> Yes, it's hard to understand why mdadm 2.6.7 is current in 9.04 and not 2.6.8. It's also amazing you can recover without loss of data by using it, from the kind of thing you went through with your MB. In all the years of using mdadm I've not had to go through what you did. <smile>

I'll look to see what version is in 9.10 when Beta comes out.

2.6.8 is not the latest version of mdadm. The latest is 3.0 and looking at the git repository, seems like 3.1 (or 3.0.1?) is coming soon.

I've had my share of agony before. Corrupted XFS filesystem due to damaged disk when the array was degraded, but used "dd" to clone that disk and I lost just the files that were on the bad sectors. About 20GB out of 5.5TB, and I knew what I lost, too, so it wasn't too bad. Except for the 2 weeks of frustration...

---

### Post by fjgaude on 2009-09-10
There is lots of reasons why the latest issues of packages are not in Ubuntu repository, one being they haven't been fully tested. Over the years I've seen enough of that too.

---

