---
title: "MDADM - Replaced faulty drive now going around in cirlces"
date: 2014-02-19
forum: Server Platforms
---

### Post by Dethecus on 2014-02-19
**Apologies for the giant wall of text incoming**
I have spent hours googling and trying things with no avail, hopefully someone can assist me and I will shower them with gratitude.

I'm running 7 drives in a raid 5 array, was working perfectly for several years until the other day one of the drives died.
I located the faulty drive using the power of google and figuring out the serial number with *hdparm -i /dev/sdx*
Replaced drive, booted, copied partition information from one of the other drives, attempted to add it to the array.
It gave me grief over various things which I have tried to get around to no avail.

In the end I've gone with creating from scratch with:
*mdadm --create /dev/md0 -v -l 5 -n 7 /dev/sda1 /dev/sdb1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1*
Which was successful. Then I tried assembling with:
*mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1*
Which was also successful.

It then goes through this:
[I]root@Avatar:/home/dethecus# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdh1[7] sdg1[5] sdf1[4] sde1[3] sdd1[2] sdb1[1] sda1[0]
      4395431424 blocks level 5, 64k chunk, algorithm 2 [7/6] [UUUUUU_]
      [>....................]  recovery =  0.5% (3851440/732571904) finish=890.9min speed=13628K/sec[/I]

Which as you can see takes upwards of 14 hours, much like the first time I built the array several years ago.
The problem is that it is still showing one of the drives as failed even though I have replaced the faulty drive.
I can even confirm that this was the faulty drive as I unplugged it and the *[UUUUUU_]* remained the same but if I unplugged another drive it would fail to assemble at all.
I have tested another SATA cable with no change.
I have tried swapping the SATA ports over but it is still the same drive (different /dev/sdx but same serial number) showing as failed.

When it finishes recovering it just goes back to the same damn thing, won't assemble the array like below:
[I]mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1
mdadm: cannot open device /dev/sdf1: Device or resource busy
mdadm: /dev/sdf1 has no superblock - assembly aborted
[/I]

I have been through this process twice now, waiting a full 14 goddamn hours each time only to be back at square one.
I can't assemble the array as you normally would due to one of them not having a superblock, other people have had success creating from scratch as I have tried but I have just been going in circles :confused:

Relevant information that I know I will be asked for:
```
root@Avatar:/home/dethecus# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdh1[7] sdg1[5] sdf1[4] sde1[3] sdd1[2] sdb1[1] sda1[0]
      4395431424 blocks level 5, 64k chunk, algorithm 2 [7/6] [UUUUUU_]
      [>....................]  recovery =  1.4% (10701796/732571904) finish=888.7min speed=13536K/sec

unused devices: <none>

root@Avatar:/home/dethecus# mdadm -E /dev/sd[abdefgh]1

dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 7f4e5e1a:3d2a30d7:6eb23176:601b0ba8 (local to host Avatar)
  Creation Time : Thu Feb 20 15:22:18 2014
     Raid Level : raid5
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
     Array Size : 4395431424 (4191.81 GiB 4500.92 GB)
   Raid Devices : 7
  Total Devices : 8
Preferred Minor : 0

    Update Time : Thu Feb 20 15:22:18 2014
          State : clean
 Active Devices : 6
Working Devices : 7
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 6274cce - correct
         Events : 0.1

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       0        0        6      faulty
   7     7       8      113        7      spare   /dev/sdh1

/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 7f4e5e1a:3d2a30d7:6eb23176:601b0ba8 (local to host Avatar)
  Creation Time : Thu Feb 20 15:22:18 2014
     Raid Level : raid5
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
     Array Size : 4395431424 (4191.81 GiB 4500.92 GB)
   Raid Devices : 7
  Total Devices : 8
Preferred Minor : 0

    Update Time : Thu Feb 20 15:22:18 2014
          State : clean
 Active Devices : 6
Working Devices : 7
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 6274ce0 - correct
         Events : 0.1

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       0        0        6      faulty
   7     7       8      113        7      spare   /dev/sdh1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 7f4e5e1a:3d2a30d7:6eb23176:601b0ba8 (local to host Avatar)
  Creation Time : Thu Feb 20 15:22:18 2014
     Raid Level : raid5
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
     Array Size : 4395431424 (4191.81 GiB 4500.92 GB)
   Raid Devices : 7
  Total Devices : 8
Preferred Minor : 0

    Update Time : Thu Feb 20 15:22:18 2014
          State : clean
 Active Devices : 6
Working Devices : 7
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 6274d02 - correct
         Events : 0.1

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       49        2      active sync   /dev/sdd1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       0        0        6      faulty
   7     7       8      113        7      spare   /dev/sdh1

/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 7f4e5e1a:3d2a30d7:6eb23176:601b0ba8 (local to host Avatar)
  Creation Time : Thu Feb 20 15:22:18 2014
     Raid Level : raid5
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
     Array Size : 4395431424 (4191.81 GiB 4500.92 GB)
   Raid Devices : 7
  Total Devices : 8
Preferred Minor : 0

    Update Time : Thu Feb 20 15:22:18 2014
          State : clean
 Active Devices : 6
Working Devices : 7
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 6274d14 - correct
         Events : 0.1

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       65        3      active sync   /dev/sde1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       0        0        6      faulty
   7     7       8      113        7      spare   /dev/sdh1

/dev/sdf1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 7f4e5e1a:3d2a30d7:6eb23176:601b0ba8 (local to host Avatar)
  Creation Time : Thu Feb 20 15:22:18 2014
     Raid Level : raid5
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
     Array Size : 4395431424 (4191.81 GiB 4500.92 GB)
   Raid Devices : 7
  Total Devices : 8
Preferred Minor : 0

    Update Time : Thu Feb 20 15:22:18 2014
          State : clean
 Active Devices : 6
Working Devices : 7
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 6274d26 - correct
         Events : 0.1

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       81        4      active sync   /dev/sdf1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       0        0        6      faulty
   7     7       8      113        7      spare   /dev/sdh1

/dev/sdg1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 7f4e5e1a:3d2a30d7:6eb23176:601b0ba8 (local to host Avatar)
  Creation Time : Thu Feb 20 15:22:18 2014
     Raid Level : raid5
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
     Array Size : 4395431424 (4191.81 GiB 4500.92 GB)
   Raid Devices : 7
  Total Devices : 8
Preferred Minor : 0

    Update Time : Thu Feb 20 15:22:18 2014
          State : clean
 Active Devices : 6
Working Devices : 7
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 6274d38 - correct
         Events : 0.1

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     5       8       97        5      active sync   /dev/sdg1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       0        0        6      faulty
   7     7       8      113        7      spare   /dev/sdh1

/dev/sdh1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 7f4e5e1a:3d2a30d7:6eb23176:601b0ba8 (local to host Avatar)
  Creation Time : Thu Feb 20 15:22:18 2014
     Raid Level : raid5
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
     Array Size : 4395431424 (4191.81 GiB 4500.92 GB)
   Raid Devices : 7
  Total Devices : 8
Preferred Minor : 0

    Update Time : Thu Feb 20 15:22:18 2014
          State : clean
 Active Devices : 6
Working Devices : 7
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 6274d46 - correct
         Events : 0.1

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     7       8      113        7      spare   /dev/sdh1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       0        0        6      faulty
   7     7       8      113        7      spare   /dev/sdh1

root@Avatar:/home/dethecus# fdisk -l
Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d18f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       91201   732572001   83  Linux

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f282f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005dfe1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30024   241167748+  83  Linux
/dev/sdc2           30025       30401     3028252+   5  Extended
/dev/sdc5           30025       30401     3028221   82  Linux swap / Solaris

Disk /dev/sdd: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e69a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       91201   732572001   83  Linux

Disk /dev/sde: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       91201   732572001   83  Linux

Disk /dev/sdf: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001b801

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       91201   732572001   83  Linux

Disk /dev/sdg: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004fcae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       91201   732572001   83  Linux

Disk /dev/sdh: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000170c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       91201   732572001   83  Linux

Disk /dev/md0: 4500.9 GB, 4500921778176 bytes
2 heads, 4 sectors/track, 1098857856 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000


```

---

### Post by greyday on 2014-02-20
Did you --fail the dead drive out of the array?  The proper approach would be to --fail (even though it's already marked as failed) and --remove the drive first, then --add your new drive to the array and let it rebuild.

Example: [http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array](http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array)

So --fail and --remove sdf1 out of the array, --zero-superblock on sdf1, then --add it to the RAID.  Assuming that's the blank drive you're trying to re-add to replace the previously failed drive?  If not, not sure what to tell you, as two drives removed from a RAID5 is pretty much a scrapped RAID (though if it finished rebuilding, you are probably ok).

---

### Post by Dethecus on 2014-02-21
AHA I FIXED IT!
If you put *--assume-clean* on the end of the create command it all comes together.

```

root@Avatar:/home/dethecus# mdadm --create /dev/md0 --lev=5 --raid-devices=7 /dev/sd[abdefgh]1 --assume-clean
mdadm: /dev/sda1 appears to be part of a raid array:
    level=raid5 devices=7 ctime=Thu Feb 20 15:22:18 2014
mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid5 devices=7 ctime=Thu Feb 20 15:22:18 2014
mdadm: /dev/sdd1 appears to be part of a raid array:
    level=raid5 devices=7 ctime=Thu Feb 20 15:22:18 2014
mdadm: /dev/sde1 appears to be part of a raid array:
    level=raid5 devices=7 ctime=Thu Feb 20 15:22:18 2014
mdadm: /dev/sdf1 appears to be part of a raid array:
    level=raid5 devices=7 ctime=Thu Feb 20 15:22:18 2014
mdadm: /dev/sdg1 appears to be part of a raid array:
    level=raid5 devices=7 ctime=Thu Feb 20 15:22:18 2014
mdadm: /dev/sdh1 appears to be part of a raid array:
    level=raid5 devices=7 ctime=Thu Feb 20 15:22:18 2014
Continue creating array?
Continue creating array? (y/n) y
mdadm: array /dev/md0 started.

root@Avatar:/home/dethecus# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdh1[6] sdg1[5] sdf1[4] sde1[3] sdd1[2] sdb1[1] sda1[0]
      4395431424 blocks level 5, 64k chunk, algorithm 2 [7/7] [UUUUUUU]

unused devices: <none>

```

---

### Post by Dethecus on 2014-02-21
Not that it mattered in the end.
Spent several hours battling with xfs_repair and manually zero'ing inodes that were screwed.
In the end it just wouldn't repair any further no matter what I did, all data is kaput.
Starting from scratch, this time with ext4...

---

### Post by kosmokramer314 on 2014-02-21
> **Dethecus said:**
> Not that it mattered in the end.
Spent several hours battling with xfs_repair and manually zero'ing inodes that were screwed.
In the end it just wouldn't repair any further no matter what I did, all data is kaput.
Starting from scratch, this time with ext4...

O_O  thanks for the warning.  I've got a similar setup but went with EXT4 to begin with.  Would it have helped if you had created and saved backup superblocks before the crash?  I was paranoid and created 3 or 4 I think.

---

### Post by Dethecus on 2014-02-22
Well I used XFS on a whim because I heard it was better at handling larger files.
I have nothing against XFS but it was definitely the wrong choice to use in my situation as it doesn't handle power loss or forced restarts very well.
I have also discovered after a week of fighting with this that I actually had **two** dead hard drives, this did not help matters at all.
Also I didn't know you could backup super blocks, I may have to look into this!

---

