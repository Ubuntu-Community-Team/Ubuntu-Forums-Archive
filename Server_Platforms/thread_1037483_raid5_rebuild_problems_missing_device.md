---
title: "raid5 rebuild problems: missing device"
date: 2009-01-11
forum: Server Platforms
---

### Post by ljwobker on 2009-01-11
I've been messing around with mdadm, trying to learn it well enough that I actually feel comfortable using it as my main backup fileserver.  I've been adding and removing and reinstalling ubuntu on my test machine for a week or so, and managed to get the box into a state where I'm not sure what to do.  The current status is three disks sd[a-c], where sda is 1TB and the other two are 120GB.  The idea was to migrate from a 3x120G array to a 2x1TB array and this is a partial step.

Somehow I've gotten myself to where I have what mdadm thinks is a fully functioning array -- I'm assuming that this is working because it found the metadata on the drives and reassembled the drives by itself -- I certainly didn't tell it to.  ;-)

The problem is that this "new" device doesn't show up as a device in the output of mdadm --detail and cat /proc/mdstat
```
 /dev/md0:
        Version : 01.01
  Creation Time : Sun Jan 11 14:59:44 2009
     Raid Level : raid5
     Array Size : 224604544 (214.20 GiB 230.00 GB)
  Used Dev Size : 224604544 (214.20 GiB 230.00 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Jan 11 20:49:42 2009
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           Name : lwobker-filer:0  (local to host lwobker-filer)
           UUID : 18ea0530:58f3711e:e46d7976:55c6d5a9
         Events : 4848

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync           [COLOR=Red]<<-- NOTE NOTHING HERE?[/COLOR]
       1       8       17        1      active sync   /dev/sdb1
       4       8       33        2      active sync   /dev/sdc1

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid1
0]
md0 : active raid5 sda1[0] sdc1[4] sdb1[1]
      224604544 blocks super 1.1 level 5, 64k chunk, algorithm 2 [3/3] [UUU]
```Now to me, here's the really strange part.  The first device in the array SHOULD be /dev/sda1 -- but it doesn't show up that way.  The device is there, and it's working, because I have verified the checksums of the files on the array and they're correct -- unless I'm totally insane you can't get the same "md5sum" for a file unless it's actually the whole/correct file... and the md5sums are correct for about 100 files on this array  ;-)

So the problem is, right now, I can't manage anything that has to do with /dev/sda1.  I can't mark it faulty, I can't fail it, I can't remove it from the array, etc... I can't seem to figure out how to address the drive so that I can manage it normally... 

anyone have suggestions as to what to try next?  I can always rebuild the array, but since the point of this whole exercise for me is to learn this stuff, I figured I'd ask.

---

### Post by fjgaude on 2009-01-12
I'm not sure what is going on with your setup... The 1T drive would normally be seen as 120G in the raid5 array.

Did you fault a drive, remove it, and then add the 1T one into the array?

Here's a good link to just about covering just about all there is to know, all things to do with **mdadm**:

[http://linux-raid.osdl.org/index.php/Detecting%2C_querying_and_testing](http://linux-raid.osdl.org/index.php/Detecting%2C_querying_and_testing)

I like how you are going about testing and learning... keep it up!

---

