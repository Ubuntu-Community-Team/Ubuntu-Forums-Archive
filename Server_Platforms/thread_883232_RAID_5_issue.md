---
title: "RAID 5 issue"
date: 2008-08-07
forum: Server Platforms
---

### Post by aaronanderson on 2008-08-07
I would like to bounce some ideas regarding attempting to recover my RAID 5 array (4 disks) with the group. I had backed up all of the critical data, but not the "nice to have" data.

First, sorry for the length of the post. I'm trying to provide as much information as possible.

Background:
On Friday I came home to errors on the console saying "Unable to write to swap space". I attempted to scroll up but there was no other useful information. Essentially the buffer was full of the same message.
Rebooted, it just hung while attempting to assemble the array.
Attempted to use Ubuntu Live CD, kernel output tons of controller errors and boot-up wouldn't complete.
Used the System Rescue CD and was able to get to a prompt.
Attempted to assemble the array, which failed due to insufficient disks.
Searched googled and found some posts that mentioned forcing the assembly. This was probably a bad idea but I was also some what panicking. :)
The array assembled but dropped 1 disk almost immediately (which should be fine). I started running a fsck on the file system, however, the array dropped a second disk. The array was also in the middle of a reshape (or recovery) when the second disk was dropped.

To be safe I purchased a new motherboard (I was initially convinced it was a controller error) and new disks. I have built a new array to start from scratch while I attempt to recover the old array.

I have dd_resucue'd the partitions (not the entire drive) on to files on my new array. 3 of the 4 disks imaged without errors, only 1 disk presented several errors. The stats from dd_rescue are:
xfered: 243850640K
success xfer: 243850496K
errors: 288
error size: 144K
Ultimately 144K out of 243850640K is a small percentage.

I setup loopback devices and attempted to assemble to array, without any luck. Results:
```

mdadm: looking for devices for /dev/md1
mdadm: /dev/loop0 is identified as a member of /dev/md1, slot 0.
mdadm: /dev/loop1 is identified as a member of /dev/md1, slot 1.
mdadm: /dev/loop2 is identified as a member of /dev/md1, slot 2.
mdadm: /dev/loop3 is identified as a member of /dev/md1, slot 4.
mdadm: added /dev/loop1 to /dev/md1 as 1
mdadm: added /dev/loop2 to /dev/md1 as 2
mdadm: no uptodate device for slot 3 of /dev/md1
mdadm: added /dev/loop3 to /dev/md1 as 4
mdadm: added /dev/loop0 to /dev/md1 as 0
mdadm: /dev/md1 assembled from 2 drives and 1 spare - not enough to start the array.

```

Question:
I've been reading tons of articles over the last week about RAID 5 recovery and few of them are promising. I'm hoping that I'm in a better boat because 3 of the 4 disks imaged without error and the errors on the other disk are minimal (I realize it only takes 1 bad block in the wrong place but I'm crossing my fingers). I'm hoping that the problem is just with the meta-data for the array.

The meta-data for the various elements of the array are as follows:
```

/dev/loop0:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 2b3c4f62:dbb0fdec:e368bf24:bd0fce41
  Creation Time : Sat Feb 16 07:30:12 2008
     Raid Level : raid5
  Used Dev Size : 243850560 (232.55 GiB 249.70 GB)
     Array Size : 731551680 (697.66 GiB 749.11 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sat Aug  2 10:00:11 2008
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 1
       Checksum : ef6694c8 - correct
         Events : 0.2632

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        2        0      active sync   /dev/sda2

   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       34        1      active sync   /dev/sdc2
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       50        4      spare   /dev/sdd2

```

```

/dev/loop1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 2b3c4f62:dbb0fdec:e368bf24:bd0fce41
  Creation Time : Sat Feb 16 07:30:12 2008
     Raid Level : raid5
  Used Dev Size : 243850560 (232.55 GiB 249.70 GB)
     Array Size : 731551680 (697.66 GiB 749.11 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sat Aug  2 10:00:11 2008
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 1
       Checksum : ef6694ea - correct
         Events : 0.2632

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       34        1      active sync   /dev/sdc2

   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       34        1      active sync   /dev/sdc2
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       50        4      spare   /dev/sdd2

```

```

/dev/loop2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 2b3c4f62:dbb0fdec:e368bf24:bd0fce41
  Creation Time : Sat Feb 16 07:30:12 2008
     Raid Level : raid5
  Used Dev Size : 243850560 (232.55 GiB 249.70 GB)
     Array Size : 731551680 (697.66 GiB 749.11 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Aug  1 16:06:59 2008
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 1
       Checksum : ef659945 - correct
         Events : 0.2626

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       34        2      active sync   /dev/sdc2

   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       18        1      active sync   /dev/sdb2
   2     2       8       34        2      active sync   /dev/sdc2
   3     3       0        0        3      faulty removed
   4     4       8       50        4      spare   /dev/sdd2

```

```

/dev/loop3:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 2b3c4f62:dbb0fdec:e368bf24:bd0fce41
  Creation Time : Sat Feb 16 07:30:12 2008
     Raid Level : raid5
  Used Dev Size : 243850560 (232.55 GiB 249.70 GB)
     Array Size : 731551680 (697.66 GiB 749.11 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sat Aug  2 10:00:11 2008
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 1
       Checksum : ef6694fa - correct
         Events : 0.2632

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       50        4      spare   /dev/sdd2

   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       34        1      active sync   /dev/sdc2
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       50        4      spare   /dev/sdd2

```

I'm curious if it's possible to have mdadm re-assemble the array based on the information I provided. Since I have images of the disk, I can test out any theory. My thoughts are:
- edit the raid meta-data such that all of the drives appear active
- manually create a new image based on concatenating each data block from each stripe together. Probably use something like the raidextract utility mentioned in this article ([link]("http://www.chiark.greenend.org.uk/~peterb/linux/raidextract/")) or what this clever fellow did in this article ([link]("http://www.intelligentedu.com/how_to_recover_from_a_broken_raid5.html")).

Also the Events field in the meta data differs for loop2 (represents sdc2). I haven't figured out what Events tracks but I remember reading something that stated if the number is off by more than 2, that drive will not be used in the array.

Any guidance is greatly appreciated.

---

### Post by aaronanderson on 2008-08-08
So I believe I made a little progress. I looked at the utilities mentioned in this [link]("http://www.chiark.greenend.org.uk/~peterb/linux/raidextract/").

raidextract required me to know which disk the parity began on. parityinfo gave me this information:
```

$ ./parityinfo.static --length $((1024*64000)) /dev/loop0 /dev/loop1 /dev/loop2 /dev/loop3  | head -40
Length of stripe across all disks (except parity): 196608
Number of disks: 4
Reading from all disks, position 0 to 131071 (stripe 0 to 1)

Output position 0 (stripe 0)
  data disk=1 /dev/loop1
  parity disk=0 /dev/loop0
  data 0 (stripe 0) [0..65535]

Output position 65536 (stripe 1)
  data disk=2 /dev/loop2
  parity disk=0 /dev/loop0
  data 0 (stripe 0) [0..65535]

Output position 131072 (stripe 2)
  data disk=3 /dev/loop3
  parity disk=0 /dev/loop0
  data 0 (stripe 0) [0..65535]

Output position 196608 (stripe 3)
  data disk=0 /dev/loop0
  parity disk=1 /dev/loop1
  data 65536 (stripe 1) [0..65535]

```

I ran raidextract with the following command:
```

sudo ./raidextract.static --rotate 0 --length $((32*1024*64000)) /dev/loop0 /dev/loop1 /dev/loop2 /dev/loop3 > test

```

The result is:
```

raidextract.static: Parity check failed at disk positition 2424324 at byte 65028

```

I then used parityinfo to determine the disk where the parity fails:
```

./parityinfo.static --start 2400000 --length $((2*1024*64000)) /dev/loop0 /dev/loop1 /dev/loop2 /dev/loop3 | head -50
Length of stripe across all disks (except parity): 196608
Number of disks: 4
Reading from all disks, position 786432 to 917503 (stripe 12 to 13)

Output position 2400000 (stripe 36)
  data disk=1 /dev/loop1
  parity disk=0 /dev/loop0
  data 786432 (stripe 12) [40704..65535]

Output position 2424832 (stripe 37)
  data disk=2 /dev/loop2
  parity disk=0 /dev/loop0
  data 786432 (stripe 12) [0..65535]

```

It appears that the parity checks fails on a block on disk 1. I re-run raidextract specifying that disk 1 failed:
```

sudo ./raidextract.static --failed 1 --rotate 0 --length $((32*1024*64000)) /dev/loop0 /dev/loop1 /dev/loop2 /dev/loop3 > test

```

It spits several parity errors (~50-75) but then continues on. Since the program continues and doesn't stop, my understanding is that it is able to account for the bad parity on drive 1 using the blocks from the other disks in that stripe. I let it run through for a bit and stopped it around 2GB of output. My understanding is that the output should represent an assembled array. I try to mount it, but encounter problems:
```

$ mount -o loop test /mnt
mount: you must specify the filesystem type

```

If I try and run a fsck, I get errors:
```

$ losetup /dev/loop5 test
$ fsck.ext2 /dev/loop5
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/loop5

```

When I try to specify another superblock location, I get an odd error that it can't open the device:
```

$ fsck.ext2 -b 32768 /dev/loop5
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Device or resource busy while trying to open /dev/loop5
Filesystem mounted or opened exclusively by another program?

```

A strace points to the fact that it can't open the device exclusively:
```

open("/dev/loop4", O_RDWR|O_EXCL)       = -1 EBUSY (Device or resource busy)
open("/dev/loop4", O_RDWR|O_EXCL)       = -1 EBUSY (Device or resource busy)
open("/dev/loop4", O_RDWR|O_EXCL)       = -1 EBUSY (Device or resource busy)
open("/dev/loop4", O_RDWR|O_EXCL)       = -1 EBUSY (Device or resource busy)
open("/dev/loop4", O_RDWR|O_EXCL)       = -1 EBUSY (Device or resource busy)
open("/dev/loop4", O_RDWR|O_EXCL)       = -1 EBUSY (Device or resource busy)

```

lsof doesn't point to anything necessarily:
```

$ lsof | grep loop5
loop5      2779        root  cwd       DIR                9,0         4096                  256 /
loop5      2779        root  rtd       DIR                9,0         4096                  256 /
loop5      2779        root  txt   unknown                                                      /proc/2779/exe

$ ps waux | grep 2779
root      2779  0.0  0.0      0     0 ?        S<   23:15   0:00 [loop5]
root      2807  0.0  0.0   5164   832 pts/0    R+   23:19   0:00 grep 2779

```

More research required.

---

### Post by aaronanderson on 2008-08-08
I figured out why /dev/loop4 was busy. I had it as part of the non-active md1 array. I stopped it and it's all good.


I did more research and found out about the --run switch. I ran:
```

$ mdadm -v -A --force --run /dev/md1 /dev/loop0 /dev/loop2 /dev/loop3
mdadm: forcing event count in /dev/loop2(2) from 2626 upto 2632
mdadm: clearing FAULTY flag for device 1 in /dev/md1 for /dev/loop2
mdadm: looking for devices for /dev/md1
mdadm: /dev/loop0 is identified as a member of /dev/md1, slot 0.
mdadm: /dev/loop2 is identified as a member of /dev/md1, slot 2.
mdadm: /dev/loop3 is identified as a member of /dev/md1, slot 4.
mdadm: no uptodate device for slot 1 of /dev/md1
mdadm: added /dev/loop2 to /dev/md1 as 2
mdadm: no uptodate device for slot 3 of /dev/md1
mdadm: added /dev/loop3 to /dev/md1 as 4
mdadm: added /dev/loop0 to /dev/md1 as 0
mdadm: failed to RUN_ARRAY /dev/md1: Input/output error
mdadm: Not enough devices to start the array.

```

That didn't work. I excluded /dev/loop1 since that is what raidextract mentioned as being a problem. Details of the array are:
```

$ mdadm --detail  /dev/md1
/dev/md1:
        Version : 00.90.03
  Creation Time : Sat Feb 16 07:30:12 2008
     Raid Level : raid5
  Used Dev Size : 243850560 (232.55 GiB 249.70 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sat Aug  2 10:00:11 2008
          State : active, degraded, Not Started
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 2b3c4f62:dbb0fdec:e368bf24:bd0fce41
         Events : 0.2632

    Number   Major   Minor   RaidDevice State
       0       7        0        0      active sync   /dev/loop0
       1       0        0        1      removed
       2       7        2        2      active sync   /dev/loop2
       3       0        0        3      removed

       4       7        3        -      spare   /dev/loop3

```

I tried again, but this time excluding /dev/loop3 since it is showing up as a spare.

```

$ mdadm -v -A --force --run /dev/md1 /dev/loop0 /dev/loop1 /dev/loop2
mdadm: looking for devices for /dev/md1
mdadm: /dev/loop0 is identified as a member of /dev/md1, slot 0.
mdadm: /dev/loop1 is identified as a member of /dev/md1, slot 1.
mdadm: /dev/loop2 is identified as a member of /dev/md1, slot 2.
mdadm: added /dev/loop1 to /dev/md1 as 1
mdadm: added /dev/loop2 to /dev/md1 as 2
mdadm: no uptodate device for slot 3 of /dev/md1
mdadm: added /dev/loop0 to /dev/md1 as 0
mdadm: /dev/md1 has been started with 3 drives (out of 4).

```

Bingo!!!!!!

Time to start copying the data.

---

### Post by aaronanderson on 2008-08-08
Unfortunately I didn't get very far. I know there is corruption in the sdc2 file (represented by /dev/loop2). Sure enough the minute I change directory I got the following in dmesg:
```

[192760.230409] md: super_written gets error=-5, uptodate=0
[192760.230417] raid5: Disk failure on loop1, disabling device. Operation continui                                       ng on 2 devices
[192760.230854] RAID5 conf printout:
[192760.230857]  --- rd:4 wd:2
[192760.230859]  disk 0, o:1, dev:loop0
[192760.230861]  disk 1, o:0, dev:loop1
[192760.230862]  disk 2, o:1, dev:loop2
[192760.230872] Buffer I/O error on device md1, logical block 0
[192760.230877] lost page write due to I/O error on md1
[192760.230887] Buffer I/O error on device md1, logical block 2
[192760.230891] lost page write due to I/O error on md1
[192760.230899] Buffer I/O error on device md1, logical block 5
[192760.230903] lost page write due to I/O error on md1
[192760.230910] Buffer I/O error on device md1, logical block 6
[192760.230914] lost page write due to I/O error on md1
[192760.230921] Buffer I/O error on device md1, logical block 17
[192760.230929] lost page write due to I/O error on md1
[192760.230935] Buffer I/O error on device md1, logical block 32
[192760.230942] lost page write due to I/O error on md1
[192760.230948] Buffer I/O error on device md1, logical block 33
[192760.230955] lost page write due to I/O error on md1
[192760.230962] Buffer I/O error on device md1, logical block 1027
[192760.230969] lost page write due to I/O error on md1
[192760.230976] Buffer I/O error on device md1, logical block 99331
[192760.230983] lost page write due to I/O error on md1
[192760.230990] Buffer I/O error on device md1, logical block 1638402
[192760.230997] lost page write due to I/O error on md1
[192760.233201] EXT3 FS on md1, internal journal
[192760.253900] ext3_orphan_cleanup: deleting unreferenced inode 3440802
[192760.264055] RAID5 conf printout:
[192760.264058]  --- rd:4 wd:2
[192760.264059]  disk 0, o:1, dev:loop0
[192760.264061]  disk 2, o:1, dev:loop2
[192760.284468] ext3_orphan_cleanup: deleting unreferenced inode 11223071
[192760.309362] EXT3-fs error (device md1): ext3_free_branches: Read failure, inod                                       e=11223071, block=22515381
[192760.309553] EXT3-fs error (device md1): ext3_free_branches: Read failure, inod                                       e=11223071, block=22526365
[192760.323176] ext3_orphan_cleanup: deleting unreferenced inode 3457151
[192760.353886] EXT3-fs: md1: 3 orphan inodes deleted
[192760.353889] EXT3-fs: recovery complete.
[192760.353927] journal_bmap: journal block not found at offset 12 on md1
[192760.353935] Aborting journal on device md1.
[192760.353947] __journal_remove_journal_head: freeing b_committed_data
[192760.354016] journal commit I/O error
[192760.354058] EXT3-fs: mounted filesystem with ordered data mode.
[192762.813798] ext3_abort called.
[192762.813811] EXT3-fs error (device md1): ext3_journal_start_sb: Detected aborte                                       d journal
[192762.813824] Remounting filesystem read-only
[192790.156750] printk: 199 messages suppressed.
[192790.156754] Buffer I/O error on device md1, logical block 6914049
[192790.156764] lost page write due to I/O error on md1
[192790.156771] Buffer I/O error on device md1, logical block 6914053
[192790.156778] lost page write due to I/O error on md1
[192790.156796] Buffer I/O error on device md1, logical block 6946816
[192790.156802] lost page write due to I/O error on md1
[193197.618384] EXT2-fs: md1: couldn't mount because of unsupported optional featu                                       res (4).
[193204.231862] EXT3-fs: can't read group descriptor 15
[193209.910037] Buffer I/O error on device md1, logical block 16
[193209.910054] Buffer I/O error on device md1, logical block 17
[193209.910066] Buffer I/O error on device md1, logical block 18
[193209.910079] Buffer I/O error on device md1, logical block 19
[193209.910698] Buffer I/O error on device md1, logical block 182887888
[193209.910709] Buffer I/O error on device md1, logical block 182887888
[193209.911349] EXT3-fs: can't read group descriptor 15

```

Looks like a journal problem. I attempted to remount the ext3 system as ext2. It failed because the array went degraded again. I am also not able to restart it again:
```

$ mdadm -v -A --force --run /dev/md1 /dev/loop0 /dev/loop1 /dev/loop2
mdadm: looking for devices for /dev/md1
mdadm: /dev/loop0 is identified as a member of /dev/md1, slot 0.
mdadm: /dev/loop1 is identified as a member of /dev/md1, slot 1.
mdadm: /dev/loop2 is identified as a member of /dev/md1, slot 2.
mdadm: forcing event count in /dev/loop1(1) from 2632 upto 2638
mdadm: Could not re-write superblock on /dev/loop1
mdadm: added /dev/loop1 to /dev/md1 as 1
mdadm: failed to add /dev/loop2 to /dev/md1: Invalid argument
mdadm: no uptodate device for slot 3 of /dev/md1
mdadm: failed to add /dev/loop0 to /dev/md1: Invalid argument
mdadm: failed to RUN_ARRAY /dev/md1: Input/output error
mdadm: Not enough devices to start the array.

```

More banging away.

---

### Post by aaronanderson on 2008-08-08
According to dmesg I was getting:
```

[194571.278722] md: loop2 has same UUID but different superblock to loop1
[194571.278725] md: loop2 has different UUID to loop1
[194571.278727] md: export_rdev(loop2)
[194571.279114] md: loop0 has same UUID but different superblock to loop1
[194571.279117] md: loop0 has different UUID to loop1

```

More google searching lead me to running the following:
```

mdadm --create /dev/md1 --assume-clean --level=5 --raid-devices=4 /dev/loop0 /dev/loop1 /dev/loop2 missing

```

This essentially re-built the superblock for the array and the array started. The post I got this from was [http://ubuntuforums.org/showthread.php?t=410136](http://ubuntuforums.org/showthread.php?t=410136).

Since I knew my journal on my ext3 file system was corrupt, I removed it using:
```

tune2fs -O ^has_journal /dev/md1

```

I've now mounted my file system (read-only) and started copying files off it.

---

### Post by greco8523 on 2008-09-04
This website should help you with any RAID data recovery that you may want to attempt. 

[http://www.datarecoveryadvice.org/](http://www.datarecoveryadvice.org/)

---

