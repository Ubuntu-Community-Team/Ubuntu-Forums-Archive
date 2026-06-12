---
title: "Cannot rebuild RAID-1 after one drive failed and server was reinstalled"
date: 2013-02-22
forum: Server Platforms
---

### Post by w-sky on 2013-02-22
Hi there.

I want to rebuild a RAID-1 array which was created using Ubuntu server 10.04 and was functioning fine until one drive failed.
At the same time, the system got a major upgrade with a new, fresh install of Ubuntu server 12.04 and all updates.

The server actually has two RAID-1 arrays; assembling the array that didn't fail worked fine, but I can't assemble (and then reconstruct) the other array. mdadm just refuses to do anything and does not even print an error message.

Here are some details:

```
mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 00000000:00000000:00000000:00000000
  Creation Time : Wed Jun 13 22:19:08 2012
     Raid Level : -unknown-
   Raid Devices : 0
  Total Devices : 1
Preferred Minor : 127

    Update Time : Wed Jun 13 22:32:23 2012
          State : active
 Active Devices : 0
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 1
       Checksum : bd3e3c41 - correct
         Events : 1


      Number   Major   Minor   RaidDevice State
this     0       8       33        0      spare   /dev/sdc1

   0     0       8       33        0      spare   /dev/sdc1

```
It is obvious that the empty UUID is not correct, Raid Level should not be unknown and more, but it I can not see how to fix this. I tried various commands:
```
sudo mdadm --assemble --run /dev/md3 /dev/sdc1

sudo mdadm --assemble --force /dev/md3 /dev/sdc1
```
but the result is nothing, no error message and no array /dev/md3 will appear. When I make mdadm use superblock version 0.9, this is the result:
```
sudo mdadm --assemble --run /dev/md3 /dev/sdc1 --metadata=0.9 --update=uuid
mdadm: no RAID superblock on /dev/sdc1
```
To compare, this is what "examine" looks like on a drive of the working array, which was created on the same old server as the array where a drive had failed:
```
mdadm --examine /dev/sdb2
/dev/sdb2:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 66d12491:ff445427:7014d83d:8c7a2315
  Creation Time : Tue Nov  9 17:20:11 2010
     Raid Level : raid1
  Used Dev Size : 1948630976 (1858.36 GiB 1995.40 GB)
     Array Size : 1948630976 (1858.36 GiB 1995.40 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Fri Feb 22 22:29:47 2013
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 1df6dc1e - correct
         Events : 52


      Number   Major   Minor   RaidDevice State
this     0       8       18        0      active sync   /dev/sdb2

   0     0       8       18        0      active sync   /dev/sdb2
   1     1       8       50        1      active sync   /dev/sdd2
```

As I don't know what to do next, any help is appreciated a lot.

If it might help, here is mdstat showing the working array, which has 3 partitions.
(md0=original data partition, md1=newly created swap partition, md2=newly created system partition)
```
cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdd2[1] sdb2[0]
      1948630976 blocks [2/2] [UU]
      
md1 : active raid1 sdb1[0] sdd1[1]
      976551 blocks super 1.2 [2/2] [UU]
      
md2 : active raid1 sdb3[0] sdd3[1]
      3904896 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>
```
Also I tried to mount sdc1 as a single drive, but it does not compute:
```
sudo mount /dev/sdc1 foo/
mount: unknown file system type „linux_raid_member“
```
:x

---

### Post by darkod on 2013-02-22
First, is sdc1 a new blank partition (disk)? One of the messages said no superblock found on sdc1 which could explain the zero UUID and no raid level.

Second, you can't try (force) md3 to assemble from one partition (member). You have to try with both even if one is failed. Or replace the failed with missing. Something like that.

Which are the partitions that md3 was made of? Where are they now?

I think it would have been much easier if you replaced the failed disk first, let the arrays sync, and only then do a fresh clean install. Like this if you didn't specify md3 during the install, it doesn't know anything about it and you have to fish for it.

PS. I just re-read it, it seems the no superblock message was only when you forced it to use metadata version 0.90. But the other questions remains, most importantly, is this the good partition of the old array? The events counter is only 1, that doesn't sound right for a partition that has been used in raid. It should have more events I think.

---

### Post by w-sky on 2013-02-22
> **darkod said:**
> First, is sdc1 a new blank partition (disk)? One of the messages said no superblock found on sdc1 which could explain the zero UUID and no raid level.
sdc1 is the original member of the array (and the only partition on sdc). Probably/hopefully it still contains all data - the drive has not been modified or written to after the failure of the other drive (sda), which now is replaced with an empty drive.

> Second, you can't try (force) md3 to assemble from one partition (member). You have to try with both even if one is failed. Or replace the failed with missing. Something like that.
Did I misunderstand the manual then? -R, --run: "Attempt to start the array even if fewer drives were given than were present last time the array was active." I thought it is possible to mount the array with just one drive, so that I can use **raidhotadd /dev/md3 /dev/sda** to reconstruct the other drive.

> Which are the partitions that md3 was made of? Where are they now?
That is sda1 (broken drive, replaced) and sdc1 (probably intact...)

> I think it would have been much easier if you replaced the failed disk first, let the arrays sync, and only then do a fresh clean install. Like this if you didn't specify md3 during the install, it doesn't know anything about it and you have to fish for it.
Yes, you are right, md3 was not specified during install. There is a reason: The old (10.04) system installation was running from an USB flash drive(!) which was starting to disintegrate just before I got the replacement HDD.


One more thing, might be important: All HDDs are partitioned with GPT.

---

### Post by darkod on 2013-02-22
The gpt table doesn't change much, just don't forget to later add sda1 as a member, not /dev/sda (the whole disk).

You might be right, I haven't used the --run option so far.

What you can also do is doing the --create as if new, but using the --asume-clean option. This is very important, if you don't use this option it will create a new array destroying any data that might be on sdc1.

Double check in tutorials and google, but I think the command in that case should be something like:
```
sudo mdadm --create /dev/md3 --assume-clean --level=1 --raid-devices=2 missing /dev/sdc1
```

That should create it with a missing slot that will be used for sda1 later.

I think the --assume-clean is the last option after you have tried --assemble with --run and --force.
Double check the syntax, and whether that option does what you need, but I think it does and that it's the last option right now.

---

### Post by w-sky on 2013-02-22
Wow, thanks Darko, that worked finally! Just one change, I had to add the option for metadata version 0.9 (because it was 0.9 before I guess). Initially mdadm created v1.2 metadata, but I was unable to mount or fsck the md device then. So I stopped it and did it again with the command line below; first mount failed once more, but one round of fsck did help.

```
sudo mdadm --create /dev/md3 --assume-clean --level=1 --raid-devices=2 --metadata=0.9 missing /dev/sdc1
```

Now I can access all data and recreate a proper RAID-1. :)

---

