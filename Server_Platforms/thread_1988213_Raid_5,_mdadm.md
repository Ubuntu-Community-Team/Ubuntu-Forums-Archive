---
title: "Raid 5, mdadm"
date: 2012-05-27
forum: Server Platforms
---

### Post by Wazz72 on 2012-05-27
My Raid 5 array (4 1tb Disks WD10EARS) had was showing as degraded. I looked and one of the disks wasnt installed, so i re-added it with the mdadm add command.
  the array is now showing as (null)Array , but cant be mounted
  [B]
if i run:[/B]

  root@warren-P5K-E:/home/warren# sudo mdadm --misc --detail /dev/md0
 **I get:**
  mdadm: cannot open /dev/md0: No such file or directory   [B]
and running:[/B]
  root@warren-P5K-E:/home/warren# cat /proc/mdstat    [B]
gives me:[/B]
  Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]  unused devices: < none >

root@warren-P5K-E:/home/warren# mdadm --examine /dev/sda /dev/sda:
Magic : a92b4efc
Version : 0.90.00
UID : 00000000:00000000:00000000:00000000
Creation Time : Sat May 26 12:08:14 2012
Raid Level : -unknown-
Raid Devices : 0
Total Devices : 4
Preferred Minor : 0 
Update Time : Sat May 26 12:08:40 2012
State : active
Active Devices : 0
Working Devices : 4
Failed Devices : 0
Spare Devices : 4
Checksum : 82d5b792 - correct
Events : 1
Number   Major   Minor   RaidDevice State
this     1       8        0        1      spare   /dev/sda
0     0       8       16        0      spare   /dev/sdb
1     1       8        0        1      spare   /dev/sda
2     2       8       32        2      spare   /dev/sdc
3     3       8       48        3      spare   /dev/sdd

root@warren-P5K-E:/home/warren# mdadm --examine /dev/sdb
/dev/sdb:
Magic : a92b4efc
Version : 0.90.00
UUID : 00000000:00000000:00000000:00000000
Creation Time : Sat May 26 12:08:14 2012
Raid Level : -unknown-
Raid Devices : 0
Total Devices : 4
Preferred Minor : 0
Update Time : Sat May 26 12:08:40 2012
State : active
Active Devices : 0
Working Devices : 4
Failed Devices : 0
Spare Devices : 4
Checksum : 82d5b7a0 - correct
Events : 1
Number   Major   Minor   RaidDevice State
this     0       8       16        0      spare   /dev/sdb
0     0       8       16        0      spare   /dev/sdb
1     1       8        0        1      spare   /dev/sda
2     2       8       32        2      spare   /dev/sdc
3     3       8       48        3      spare   /dev/sdd

 
root@warren-P5K-E:/home/warren# mdadm --examine /dev/sdc
 /dev/sdc:

Magic : a92b4efc
Version : 0.90.00
UUID : 00000000:00000000:00000000:00000000
Creation Time : Sat May 26 12:08:14 2012
Raid Level : -unknown-
Raid Devices : 0
Total Devices : 4
Preferred Minor : 0
Update Time : Sat May 26 12:08:40 2012
State : active
Active Devices : 0
Working Devices : 4
Failed Devices : 0
Spare Devices : 4
Checksum : 82d5b7b4 - correct
Events : 1
Number   Major   Minor   RaidDevice State
this     2       8       32        2      spare   /dev/sdc
0     0       8       16        0      spare   /dev/sdb
1     1       8        0        1      spare   /dev/sda
2     2       8       32        2      spare   /dev/sdc
3     3       8       48        3      spare   /dev/sdd

root@warren-P5K-E:/home/warren# mdadm --examine /dev/sdd
/dev/sdd:
Magic : a92b4efc
Version : 0.90.00
UUID : 00000000:00000000:00000000:00000000
Creation Time : Sat May 26 12:08:14 2012
Raid Level : -unknown-
Raid Devices : 0
Total Devices : 4
Preferred Minor : 0
Update Time : Sat May 26 12:08:40 2012
State : active
Active Devices : 0
Working Devices : 4
Failed Devices : 0
Spare Devices : 4
Checksum : 82d5b7c6 - correct
Events : 1
Number   Major   Minor   RaidDevice State
this     3       8       48        3      spare   /dev/sdd
0     0       8       16        0      spare   /dev/sdb
1     1       8        0        1      spare   /dev/sda
2     2       8       32        2      spare   /dev/sdc
3     3       8       48        3      spare   /dev/sdd

I have some important data on the array that hasn't been backed up this week yet.

When I added the spare, it said it was rebuilding the array, but I seem to have lost the /dev/MD0 

All help would be greatly appreciated.

---

### Post by darkod on 2012-05-27
I guess you tried reassembling with:
sudo mdadm --assemble --scan

But I am worried that it seems to show all disks as spare, not just one. And there seem to be two /dev/sdd devices shown. Now sure if this is a result if you didn't remove the disk before trying to add it.

---

### Post by darkod on 2012-05-27
In any case, don't take any rash decisions. I'll try to contact one raid expert, my knowledge is limited.

---

### Post by Wazz72 on 2012-05-27
Thanks Darkod,  I havnt run anything on it yet that should destroy the data.

---

### Post by rubylaser on 2012-05-27
Your UUID's are wiped out on each individual disk.  Did you just upgrade to 12.04?  I ask, because this seems to be a [new problem]("http://www.spinics.net/lists/raid/msg38567.html") on 12.04.  You can try to recreate the array with the assume-clean flag, but since your array resynced after adding the spare, I suspect your array will not be recoverable. +1 for keeping fairly recent backups though.

---

### Post by Wazz72 on 2012-05-27
I backed up the mdadm.conf file, which hase the 4 uuids in it, will I be able to do anything with them?

# definitions of existing MD arrays
ARRAY /dev/md0 UUID=78bded27:4f36b420:b8c93aaa:68704163

---

### Post by Wazz72 on 2012-05-27
It only took about 5 mins to re-sync so I don't think that it worked properly.

---

### Post by rubylaser on 2012-05-27
> **Wazz72 said:**
> I backed up the mdadm.conf file, which hase the 4 uuids in it, will I be able to do anything with them?

# definitions of existing MD arrays
ARRAY /dev/md0 UUID=78bded27:4f36b420:b8c93aaa:68704163

Unfortunately, no.  At this point the disks don't have the UUID in their superblocks, so that UUID wouldn't recognize your disks as part of the array.  And, any syncing (even a couple seconds) is enough screw up the filesystem and associated data.  You could give this a try.  This will remove the mdadm superblock (leaving the rest of the data as it is on the disk) and then you're recreating the array

```
mdadm --zero-superblock /dev/sda
mdadm --zero-superblock /dev/sdb
mdadm --zero-superblock /dev/sdc
mdadm --zero-superblock /dev/sdd
```

```
mdadm --create /dev/md0 --metadata=0.90 --assume-clean --level=5 --chunk=64 --verbose --raid-devices=4 /dev/sd[abcd] 
```

You'll need the same parameters and disk order as your original create for this to even have a chance of working.  I assume this was a RAID5 and with metadata version 0.90, your default chunk size should have been 64K.  As I said before, this would be a 1 in 1 million shot though, because your array already tried a resync.

---

### Post by Wazz72 on 2012-05-27
> **rubylaser said:**
> Unfortunately, no.  At this point the disks don't have the UUID in their superblocks, so that UUID wouldn't recognize your disks as part of the array.  And, any syncing (even a couple seconds) is enough screw up the filesystem and associated data.  You could give this a try.  This will remove the mdadm superblock (leaving the rest of the data as it is on the disk) and then you're recreating the array

```
mdadm --zero-superblock /dev/sda
mdadm --zero-superblock /dev/sdb
mdadm --zero-superblock /dev/sdc
mdadm --zero-superblock /dev/sdd
``````
mdadm --create /dev/md0 --metadata=0.90 --assume-clean --level=5 --chunk=64 --verbose --raid-devices=4 /dev/sd[abcd] 
```You'll need the same parameters and disk order as your original create for this to even have a chance of working.  I assume this was a RAID5 and with metadata version 0.90, your default chunk size should have been 64K.  As I said before, this would be a 1 in 1 million shot though, because your array already tried a resync.

Im not 100% sure that it was a re-sync, as the disk utility did it automatically, without me telling it to do it.

I assume that the end of the command is:

devices=4 /dev/sda /dev/sdb /dev/sdc /dev/sdd

Thanks for your help.

---

### Post by Wazz72 on 2012-05-27
did what you suggested, and it came back with this when I tried to mount it: Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error

---

### Post by darkod on 2012-05-27
And what does cat /proc/mdstat say now?

---

### Post by rubylaser on 2012-05-27
and what do these say?
```
mdadm --detail --scan
```
```
cat /etc/mdadm/mdadm.conf
```
You probably didn't update this or your initramfs after rebuilding, but I just want to see what you have in there.
```
mdadm -E /dev/sd[abcd]
```

---

### Post by Wazz72 on 2012-05-28
root@warren-P5K-E:/home/warren# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdd[3] sdc[2] sdb[1] sda[0]
      2930287488 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>

---

### Post by Wazz72 on 2012-05-28
root@warren-P5K-E:/home/warren# mdadm --detail --scan
ARRAY /dev/md0 metadata=0.90 UUID=a386568f:eb98e93f:498701d1:23250a3a

---

### Post by Wazz72 on 2012-05-28
root@warren-P5K-E:/home/warren# cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 UUID=78bded27:4f36b420:b8c93aaa:68704163

# This file was auto-generated on Sat, 15 Oct 2011 19:51:12 +0100
# by mkconf $Id$

---

### Post by Wazz72 on 2012-05-28
root@warren-P5K-E:/home/warren# mdadm -E /dev/sda /dev/sdb /dev/sdc /dev/sdd
/dev/sda:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : a386568f:eb98e93f:498701d1:23250a3a (local to host warren-P5K-E)
  Creation Time : Sun May 27 23:48:24 2012
     Raid Level : raid5
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
     Array Size : 2930287488 (2794.54 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon May 28 08:01:30 2012
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 7eb5a480 - correct
         Events : 1

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        0        0      active sync   /dev/sda

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd
/dev/sdb:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : a386568f:eb98e93f:498701d1:23250a3a (local to host warren-P5K-E)
  Creation Time : Sun May 27 23:48:24 2012
     Raid Level : raid5
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
     Array Size : 2930287488 (2794.54 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon May 28 08:01:30 2012
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 7eb5a492 - correct
         Events : 1

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       16        1      active sync   /dev/sdb

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd
/dev/sdc:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : a386568f:eb98e93f:498701d1:23250a3a (local to host warren-P5K-E)
  Creation Time : Sun May 27 23:48:24 2012
     Raid Level : raid5
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
     Array Size : 2930287488 (2794.54 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon May 28 08:01:30 2012
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 7eb5a4a4 - correct
         Events : 1

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       32        2      active sync   /dev/sdc

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd
/dev/sdd:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : a386568f:eb98e93f:498701d1:23250a3a (local to host warren-P5K-E)
  Creation Time : Sun May 27 23:48:24 2012
     Raid Level : raid5
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
     Array Size : 2930287488 (2794.54 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon May 28 08:01:30 2012
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 7eb5a4b6 - correct
         Events : 1

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       48        3      active sync   /dev/sdd

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd

---

### Post by rubylaser on 2012-05-28
Unfortunately, this confirms what I mentioned earlier.  When the resync occurred, it screwed up the underlying filesystem.  You have recreated a functioning array, but the filesystem that's on it is corrupt.  It's time to break out the backup, unless you feel like using a filesystem carver like Scalpel, but you'd have to sift through TB of unsorted, renamed files to put them back in their proper place.  Sorry, we couldn't get this working, but that original resync caused the problem.

---

### Post by Wazz72 on 2012-05-29
> **rubylaser said:**
> Unfortunately, no.  At this point the disks don't have the UUID in their superblocks, so that UUID wouldn't recognize your disks as part of the array.  And, any syncing (even a couple seconds) is enough screw up the filesystem and associated data.  You could give this a try.  This will remove the mdadm superblock (leaving the rest of the data as it is on the disk) and then you're recreating the array

```
mdadm --zero-superblock /dev/sda
mdadm --zero-superblock /dev/sdb
mdadm --zero-superblock /dev/sdc
mdadm --zero-superblock /dev/sdd
``````
mdadm --create /dev/md0 --metadata=0.90 --assume-clean --level=5 --chunk=64 --verbose --raid-devices=4 /dev/sd[abcd] 
```You'll need the same parameters and disk order as your original create for this to even have a chance of working.  I assume this was a RAID5 and with metadata version 0.90, your default chunk size should have been 64K.  As I said before, this would be a 1 in 1 million shot though, because your array already tried a resync.

> **darkod said:**
> And what does cat /proc/mdstat say now?

I ran a utility called testdisk on the array, and it seems to have found  some of the superblock information,  will the array be recoverable  using the following information?

Disk /dev/md0 - 3000 GB / 2794 GiB - CHS 732571872 2 4

     Partition                  Start        End    Size in sectors

  ext4                     0   0  1 732571871   1  4 5860574976 [STORAGE]
superblock 0, blocksize=4096 [STORAGE]
superblock 32768, blocksize=4096 [STORAGE]
superblock 98304, blocksize=4096 [STORAGE]
superblock 163840, blocksize=4096 [STORAGE]
superblock 229376, blocksize=4096 [STORAGE]
superblock 294912, blocksize=4096 [STORAGE]
superblock 819200, blocksize=4096 [STORAGE]
superblock 884736, blocksize=4096 [STORAGE]
superblock 1605632, blocksize=4096 [STORAGE]
superblock 2654208, blocksize=4096 [STORAGE]

To repair the filesystem using alternate superblock, run
fsck.ext4 -p -b superblock -B blocksize device

---

### Post by rubylaser on 2012-05-29
You can get alternate superblock info like this too.
```
dumpe2fs /dev/md0 | grep -i superblock
```

And, try to use it like this on a unmounted filesystem
```
e2fsck -f -b superblock_number /dev/md0
```

It won't hurt anything to try it out, but it's likely because of the sync that none of those superblocks will work either.  Try it out and post back.

---

### Post by Wazz72 on 2012-05-29
sudo mke2fs -n /dev/sda
root@warren-P5K-E:/home/warren# dumpe2fs /dev/md0 | grep -i superblock
dumpe2fs 1.42 (29-Nov-2011)
  Primary superblock at 0, Group descriptors at 1-175
  Backup superblock at 32768, Group descriptors at 32769-32943
  Backup superblock at 98304, Group descriptors at 98305-98479
  Backup superblock at 163840, Group descriptors at 163841-164015
  Backup superblock at 229376, Group descriptors at 229377-229551
  Backup superblock at 294912, Group descriptors at 294913-295087
  Backup superblock at 819200, Group descriptors at 819201-819375
  Backup superblock at 884736, Group descriptors at 884737-884911
  Backup superblock at 1605632, Group descriptors at 1605633-1605807
  Backup superblock at 2654208, Group descriptors at 2654209-2654383
  Backup superblock at 4096000, Group descriptors at 4096001-4096175
  Backup superblock at 7962624, Group descriptors at 7962625-7962799
  Backup superblock at 11239424, Group descriptors at 11239425-11239599
  Backup superblock at 20480000, Group descriptors at 20480001-20480175
  Backup superblock at 23887872, Group descriptors at 23887873-23888047
  Backup superblock at 71663616, Group descriptors at 71663617-71663791
  Backup superblock at 78675968, Group descriptors at 78675969-78676143
  Backup superblock at 102400000, Group descriptors at 102400001-102400175
  Backup superblock at 214990848, Group descriptors at 214990849-214991023
  Backup superblock at 512000000, Group descriptors at 512000001-512000175
  Backup superblock at 550731776, Group descriptors at 550731777-550731951
  Backup superblock at 644972544, Group descriptors at 644972545-644972719

theres lots of superblock info, which one would I use where you have put the Super_block part of the e2fsck command?

---

### Post by rubylaser on 2012-05-29
> **Wazz72 said:**
> sudo mke2fs -n /dev/sda
root@warren-P5K-E:/home/warren# dumpe2fs /dev/md0 | grep -i superblock
dumpe2fs 1.42 (29-Nov-2011)
  Primary superblock at 0, Group descriptors at 1-175
  Backup superblock at 32768, Group descriptors at 32769-32943
  Backup superblock at 98304, Group descriptors at 98305-98479
  Backup superblock at 163840, Group descriptors at 163841-164015
  Backup superblock at 229376, Group descriptors at 229377-229551
  Backup superblock at 294912, Group descriptors at 294913-295087
  Backup superblock at 819200, Group descriptors at 819201-819375
  Backup superblock at 884736, Group descriptors at 884737-884911
  Backup superblock at 1605632, Group descriptors at 1605633-1605807
  Backup superblock at 2654208, Group descriptors at 2654209-2654383
  Backup superblock at 4096000, Group descriptors at 4096001-4096175
  Backup superblock at 7962624, Group descriptors at 7962625-7962799
  Backup superblock at 11239424, Group descriptors at 11239425-11239599
  Backup superblock at 20480000, Group descriptors at 20480001-20480175
  Backup superblock at 23887872, Group descriptors at 23887873-23888047
  Backup superblock at 71663616, Group descriptors at 71663617-71663791
  Backup superblock at 78675968, Group descriptors at 78675969-78676143
  Backup superblock at 102400000, Group descriptors at 102400001-102400175
  Backup superblock at 214990848, Group descriptors at 214990849-214991023
  Backup superblock at 512000000, Group descriptors at 512000001-512000175
  Backup superblock at 550731776, Group descriptors at 550731777-550731951
  Backup superblock at 644972544, Group descriptors at 644972545-644972719

theres lots of superblock info, which one would I use where you have put the Super_block part of the e2fsck command?

You'd use it like this...
```
e2fsck -f -b 1605632 /dev/md0
```

This [article]("http://www.cyberciti.biz/faq/linux-find-alternative-superblocks/") gives a good overview.  You can also try to mount the array with an alternate superblock.

---

