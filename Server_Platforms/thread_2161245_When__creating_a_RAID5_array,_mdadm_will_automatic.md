---
title: "When  creating a RAID5 array, mdadm will automatically create a degraded array"
date: 2013-07-09
forum: Server Platforms
---

### Post by 65 mustang on 2013-07-09
So i have created  a 7 device raid5 device with
```
mdadm --create /dev/md0 --level=5 --raid-devices=7 /dev/sd[b-h]1
```
From the mdadm man page.
> When  creating a RAID5 array, mdadm will automatically create a degraded array with an extra spare drive.  This is because build&#8208;ing the spare into a degraded array is in general faster than resyncing the parity on a non-degraded, but not clean, array.  This feature can be overridden with the --force option.
```

mdadm --detail /dev/md0 
/dev/md0:
        Version : 1.2
  Creation Time : Tue Jul  9 20:27:36 2013
     Raid Level : raid5
     Array Size : 5859781632 (5588.32 GiB 6000.42 GB)
  Used Dev Size : 976630272 (931.39 GiB 1000.07 GB)
   Raid Devices : 7
  Total Devices : 7
    Persistence : Superblock is persistent

    Update Time : Tue Jul  9 20:27:36 2013
          State : clean, degraded 
 Active Devices : 6
Working Devices : 7
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

           Name : dalserver:0  (local to host dalserver)
           UUID : cd798370:e2a8d9ff:8b3a2154:454b57be
         Events : 0

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       81        4      active sync   /dev/sdf1
       5       8       97        5      active sync   /dev/sdg1
       6       0        0        6      removed

       7       8      113        -      spare   /dev/sdh1

```
How about that.  The man page is correct, it created a degraded raid for me.  So now do i "build the spare into a degraded array"?

---

### Post by rubylaser on 2013-07-10
This is not normal behavior after a sync.  You shouldn't have a spare device after the initial sync is complete unless something went wrong, or you passed in the --spare-devices=1 with your --create action (which you didn't).Your array status should say    [COLOR=#ff0000][FONT=monospace]clean, resyncing [/FONT][/COLOR]until the sync is complete, and then just say [COLOR=#ff0000][FONT=monospace]clean [/FONT][/COLOR]when the sync is done.  

What does /dev/sdh1 show in it's metadata?
```

mdadm -E /dev/sdh1

```

What does this show?
```

cat /etc/mdadm/mdadm.conf

```

finally, what does the SMART info look like on that disk?
```

sudo apt-get install smartmontools
smartctl -a /dev/sdh

```

[FONT=verdana][COLOR=#FF0000][SIZE=5]_**EXAMPLE**_[/SIZE][/COLOR][/FONT]
Here is a smaller example I just built in Virtualbox in Ubuntu 12.04 Server and mdadm 3.2.5 to show you what it should do.

Create a 3 disk RAID5 array.
```

root@mdadm-test:~# mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sd[bcd]1
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 512K
mdadm: size set to 1045504K
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.

```

Watch until the array is completed syncing
```

root@mdadm-test:~# watch cat /proc/mdstat

```

Look at the completed array.
```

root@mdadm-test:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Wed Jul 10 08:10:00 2013
     Raid Level : raid5
     Array Size : 2091008 (2042.34 MiB 2141.19 MB)
  Used Dev Size : 1045504 (1021.17 MiB 1070.60 MB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent


    Update Time : Wed Jul 10 08:10:06 2013
          State : clean 
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : mdadm-test:0  (local to host mdadm-test)
           UUID : 06166bb5:400e9825:43d6ea10:34921304
         Events : 18


    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       3       8       49        2      active sync   /dev/sdd1

```

Check the metadata on an individual disk
```

root@mdadm-test:~# mdadm -E /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 06166bb5:400e9825:43d6ea10:34921304
           Name : mdadm-test:0  (local to host mdadm-test)
  Creation Time : Wed Jul 10 08:10:00 2013
     Raid Level : raid5
   Raid Devices : 3


 Avail Dev Size : 2092032 (1021.67 MiB 1071.12 MB)
     Array Size : 2091008 (2042.34 MiB 2141.19 MB)
  Used Dev Size : 2091008 (1021.17 MiB 1070.60 MB)
    Data Offset : 1024 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 6d46c227:9a210f35:f71a445d:561ae516


    Update Time : Wed Jul 10 08:10:06 2013
       Checksum : 7f7f9f9 - correct
         Events : 18


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 0
   Array State : AAA ('A' == active, '.' == missing)

```

<sidenote>7 disks is a bit too many, if you value your data, to put into a RAID5 array imho.  After 6 disks, I would really suggest moving to a RAID6, or looking at something like [SnapRAID]("http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04") if this is just a large storage volume for movies, pictures, docs, and music at home.</sidenote>

---

### Post by grunge09 on 2013-07-10
Quick Question.  I have a 5 disk mdadm array (2 tb green drives)

I started w/3 drives during the OS Server install on a USB Stick.  Then I manually added 2 more drives (1 at a time) and grew the array.  All is well but my question is this.  when I do "sudo mdadm --detail /dev/md0" it says /dev/sda1, /dev/sdb1, /dev/sdd1 (dunno why it skipped C during server OS install), /dev/sde (note missing the 1), /dev/def (note again missing the 1)

Is it ok for sde & sdf to be missing the "1" did I miss a step?  I have ran ext4.fsck each time after the 20 hours grow, and no errors.  everything seems to be working fine.  

My next trick is moving to a better case (using an old chieftec full tower case I had) it's getting full. cause I have 2 more 2tb drives to install and making the transition to raid6 on the next "grow".

---

### Post by rubylaser on 2013-07-10
> **grunge09 said:**
> Quick Question.  I have a 5 disk mdadm array (2 tb green drives)

I started w/3 drives during the OS Server install on a USB Stick.  Then I manually added 2 more drives (1 at a time) and grew the array.  All is well but my question is this.  when I do "sudo mdadm --detail /dev/md0" it says /dev/sda1, /dev/sdb1, /dev/sdd1 (dunno why it skipped C during server OS install), /dev/sde (note missing the 1), /dev/def (note again missing the 1)

Is it ok for sde & sdf to be missing the "1" did I miss a step?  I have ran ext4.fsck each time after the 20 hours grow, and no errors.  everything seems to be working fine.  

My next trick is moving to a better case (using an old chieftec full tower case I had) it's getting full. cause I have 2 more 2tb drives to install and making the transition to raid6 on the next "grow".

Yes, this is fine. You just used the whole disk instead of partitions for the last two disks.  I like to use partitions, so that I can ensure that all my disks are the same size, and I won't have a disk that is slightly smaller than the rest that won't work in my array.  All that being said, a mix of partitions and whole disks will work perfectly fine.

Make sure when you do the grow to RAID6 that you use the --backup-file option to backup the critical portion at the beginning of the grow and that you write it to a different disk.

---

### Post by CharlesA on 2013-07-10
> **rubylaser said:**
> 
<sidenote>7 disks is a bit too many, if you value your data, to put into a RAID5 array imho.  After 6 disks, I would really suggest moving to a RAID6, or looking at something like [SnapRAID]("http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04") if this is just a large storage volume for movies, pictures, docs, and music at home.</sidenote>

Not to derail the thread too much, but I'm planning on running mdadm with a 3 disk RAID5 for a backup of my main server. Would SnapRAID be better for that?

Thanks for the tutorial, btw, that should help greatly.

---

### Post by rubylaser on 2013-07-10
> **CharlesA said:**
> Not to derail the thread too much, but I'm planning on running mdadm with a 3 disk RAID5 for a backup of my main server. Would SnapRAID be better for that?

Thanks for the tutorial, btw, that should help greatly.

Charles, in your case you will be backing up virtual machines that are changing constantly, SnapRAID would not be the best solution. SnapRAID is really designed for home media servers that have big files that don't change constantly, things like: movies, tv shows, pictures, documents, etc.  

Frankly, for a backup location if you don't intend to add disks in the future, I would use ZFS (if you will expand it disk-by-disk, then mdadm is a no brainer over ZFS).  That way you can keep versioned snapshots on your backup volume, and have the bit rot protection that ZFS offers. mdadm + rsnapshot will work well in this scenario too.

---

### Post by CharlesA on 2013-07-10
> **rubylaser said:**
> Charles, in your case you will be backing up virtual machines that are changing constantly, SnapRAID would not be the best solution. SnapRAID is really designed for home media servers that have big files that don't change constantly, things like: movies, tv shows, pictures, documents, etc.  

Frankly, for a backup location if you don't intend to add disks in the future, I would use ZFS (if you will expand it disk-by-disk, then mdadm is a no brainer over ZFS).  That way you can keep versioned snapshots on your backup volume, and have the bit rot protection that ZFS offers. mdadm will also work well in this scenario too.

I'm not really sure what I am going to due with the backup array at this point. The general idea was to have the main server synced to the backup server weekly, so I don't lose data in the event the one of the backup drives goes down.

I'll probably run with mdadm in that case, especially if I will need to expand the array in the future.

Sidenote: The backup server is a Dual core pentium with 8GB RAM, so it should be able to handle anything I throw at it, especially over Gigabit ethernet.

---

### Post by rubylaser on 2013-07-10
> **CharlesA said:**
> I'm not really sure what I am going to due with the backup array at this point. The general idea was to have the main server synced to the backup server weekly, so I don't lose data in the event the one of the backup drives goes down.

I'll probably run with mdadm in that case, especially if I will need to expand the array in the future.

Sidenote: The backup server is a Dual core pentium with 8GB RAM, so it should be able to handle anything I throw at it, especially over Gigabit ethernet.

Yeah, that is way overkill for mdadm or SnapRAID and would work fine even with ZFS :)  Are you going to script it to etherwake your backup box, rsync, then shut it down after successful backup + email, or are you just going to leave the backup box on 24/7?

---

### Post by CharlesA on 2013-07-10
> **rubylaser said:**
> Yeah, that is way overkill for mdadm or SnapRAID and would work fine even with ZFS :)  Are you going to script it to etherwake your backup box, rsync, then shut it down after successful backup + email, or are you just going to leave the backup box on 24/7?

I'm thinking of running a script from my main box to wake the backup machine up, wait for it to come up all the way and then rsync it. Not quite sure how I'm going to shut it down after the backup, but I don't really want it to be running 24/7 cuz it's sitting at the foot of my bed at the moment :lolflag:

I think I need a dedicated space for my servers, but such is life in an apartment. :p

EDIT: @OP: With 7 drives I would recommend going with RAID6. I just recently moved from RAID5 to RAID 6 and had two of my drives blow up in my face - one was stuck rebuilding and the other got dropped out of the array. So glad I wasn't running RAID 5 as I would have lost all of the data on the array. I did have everything backed up, so I would not have lost data, but it would have been a chore to copy all the data back to the array from backups.

---

### Post by rubylaser on 2013-07-10
> **CharlesA said:**
> I'm thinking of running a script from my main box to wake the backup machine up, wait for it to come up all the way and then rsync it. Not quite sure how I'm going to shut it down after the backup, but I don't really want it to be running 24/7 cuz it's sitting at the foot of my bed at the moment :lolflag:

I think I need a dedicated space for my servers, but such is life in an apartment. :p

All you would need to do is write a simple BASH script from your regular fileserver to etherwake the backup-box by MAC address, ping it until it responds, then test SSH to make sure that it's available, rsync from your fileserver to the backup-box (setup keyless SSH), once the rsync is done, duse ssh to the remote box to shut it down (ssh root@backup-box 'shutdown -h now').  This way you can schedule via cron to do the backup when you are off at work, or not trying to sleep, etc.

---

### Post by CharlesA on 2013-07-10
> **rubylaser said:**
> All you would need to do is write a simple BASH script from your regular fileserver to etherwake the backup-box by MAC address, ping it until it responds, then test SSH to make sure that it's available, rsync from your fileserver to the backup-box (setup keyless SSH), once the rsync is done, duse ssh to the remote box to shut it down (ssh root@backup-box 'shutdown -h now').  This way you can schedule via cron to do the backup when you are off at work, or not trying to sleep, etc.

That sounds like a plan. I plan on using keys for ssh (duh), so sending a remote command via SSH shouldn't be that hard to script. :)

---

### Post by 65 mustang on 2013-07-11
> **rubylaser said:**
> 
finally, what does the SMART info look like on that disk?
```

sudo apt-get install smartmontools
smartctl -a /dev/sdh

```


I think your guess that i have some bad drives is corect.

This one looks like the main offender.  Do you aggree?
```
root@dalserver:/dev/disk/by-id# smartctl -a /dev/sdc
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-4-amd64] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Black
Device Model:     WDC WD1002FAEX-00Z3A0
Serial Number:    WD-WCATR2712007
LU WWN Device Id: 5 0014ee 25a38c4f2
Firmware Version: 05.01D05
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Jul 10 23:11:34 2013 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x85)    Offline data collection activity
                    was aborted by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 118)    The previous self-test completed having
                    the read element of the test failed.
Total time to complete Offline
data collection:         (16200) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 187) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3037)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   189   189   051    Pre-fail  Always       -       69505
  3 Spin_Up_Time            0x0027   172   169   021    Pre-fail  Always       -       4383
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       190
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   088   088   000    Old_age   Always       -       9182
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       188
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       65
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       124
194 Temperature_Celsius     0x0022   104   094   000    Old_age   Always       -       43
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       1
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   195   195   000    Old_age   Offline      -       1099

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       60%      9182         807585
# 2  Extended offline    Completed: read failure       90%      8324         20253333
# 3  Short offline       Completed without error       00%        65         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

Something weird may be going on with this guy also.  It may be nothing.  Perhaps this drive or the controler it is on do not support as many smary features.
```
root@dalserver:/dev/disk/by-id# smartctl -a /dev/sdg
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-4-amd64] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Black
Device Model:     WDC WD1002FAEX-00Z3A0
Serial Number:    WD-WCATR0300891
Firmware Version: 0956
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Jul 10 23:09:08 2013 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Total time to complete Offline
data collection:         (    0) seconds.
Offline data collection
capabilities:              (0x00)     Offline data collection not supported.
SMART capabilities:            (0x0000)    Automatic saving of SMART data                    is not implemented.
Error logging capability:        (0x00)    Error logging NOT supported.
                    No General Purpose Logging support.

SMART Error Log not supported
SMART Self-test Log not supported
Device does not support Selective Self Tests/Logging
```

Anyway, ill tear the system down in the next few days and note which controlers are used by these two drives and replace as needed.  The second drive may still be good.  I will try moving it to another controler and see if i can get more detailed smart info.

Thanks!

---

### Post by CharlesA on 2013-07-11
The first drive looks ok, even if it is running a bit hot. You might want to take a look at [the thread]("http://ubuntuforums.org/showthread.php?t=2157352") I created asking about SMART data.

The second disk looks.. odd. I have never had a drive not give me SMART data.

EDIT: The first disk has a pending sector, so you should probably do a verify on it to see if the drive marks it as bad.

---

### Post by rubylaser on 2013-07-11
Are there any other disks connected to the same controller as /dev/sdg (that would tell you if it's the disk or a controller limitation)?  If so, do those provide SMART data or not?  Also, how about posting the other info I asked for as well regarding mdadm? :)

---

### Post by 65 mustang on 2013-07-11
> **CharlesA said:**
> The first drive looks ok, even if it is running a bit hot. You might want to take a look at [the thread]("http://ubuntuforums.org/showthread.php?t=2157352") I created asking about SMART data.

The second disk looks.. odd. I have never had a drive not give me SMART data.

EDIT: The first disk has a pending sector, so you should probably do a verify on it to see if the drive marks it as bad.

```
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
[COLOR="#FF0000"]# 1  Short offline       Completed: read failure       60%      9182         807585
# 2  Extended offline    Completed: read failure       90%      8324         20253333[/COLOR]
# 3  Short offline       Completed without error       00%        65         -
```
These lines in red are the ones that I am worried about.  Doesn't that mean the drive is bad?

How do i "verify it" as you said.  Run the LONG test?

---

### Post by CharlesA on 2013-07-11
Yikes! I did not see that part. Is that drive still under warranty? I'd run the WD Life Guard tools to verify it is bad and RMA that sucker.

Only problem is I only found the Life Guard tools for Windows and Dos. :|

---

### Post by 65 mustang on 2013-07-11
> **rubylaser said:**
> Are there any other disks connected to the same controller as /dev/sdg (that would tell you if it's the disk or a controller limitation)?  If so, do those provide SMART data or not?  Also, how about posting the other info I asked for as well regarding mdadm? :)
I was going to but I have since destroyed the array and recreated it with RAID6 as you suggested.  I ran the same thing as before just with raid6
```
mdadm --create /dev/md0 --level=6 --raid-devices=7 /dev/sd[b-h]1
```
Surprisingly the raid created without any issues much like your example.  All drives were active and it started doing its first sync.  Although the speed was only 150K/s.  So i started looking for the bad drives as you suggested and found those two that stood out.

---

### Post by rubylaser on 2013-07-11
Yeah, 150K/s is really slow, that will take forever to sync :) If you really want to test those two disks, I'd suggest you break the array again, and test them both with badblocks at a minimum like this.

```
badblocks -wsv /dev/sdX 
```

---

### Post by CharlesA on 2013-07-11
> **rubylaser said:**
> Yeah, 150K/s is really slow, that will take forever to sync :) If you really want to test those two disks, I'd suggest you break the array again, and test them both with badblocks at a minimum like this.

```
badblocks -wsv /dev/sdX 
```

Glad you mentioned it, I'm currently running badblocks on the 2TB drives in the old array. It's current been running for almost 36 hours now. I am preforming a destructive write test on the drives all at the same time, so the I/O is probably insane.

EDIT: I used the destructive write command found here:
[https://calomel.org/badblocks_wipe.html](https://calomel.org/badblocks_wipe.html)

---

### Post by rubylaser on 2013-07-11
I'm in the process of modifying the UnRAID [preclear_disk.sh]("http://lime-technology.com/forum/index.php?topic=2817.0") script to test drives.  I like it because it compares before, mid, and after SMART values and does a pretty good job of hammering a disk to weed out marginal disks.  I'm almost done modifying it to remove all the UnRAID specific steps.  It still needs a lot more cleanup, but it works as is right now.

If a disk can make it through all of that without an issue, it should be safe to use.  I've thought about adding a badblocks destructive write to the middle, but that would be unnessecary, because it's already reading the whole disk twice and writing zeroes to the whole disk.

---

### Post by CharlesA on 2013-07-11
Cool. I just looked at what the script is designed to do and it sure seems like it would be a good way to make sure a disk is ok/safe to use. Are you going to make a blog post about it?

---

### Post by rubylaser on 2013-07-11
> **CharlesA said:**
> Cool. I just looked at what the script is designed to do and it sure seems like it would be a good way to make sure a disk is ok/safe to use. Are you going to make a blog post about it?

I will once I get it doing everything I want it to with all the unnecessary options ripped out.  It will probably be another week or so before I can release it, because to test the script, I need to let it run.  Even on the 160GB disk I'm running it on that can R/W around 120MB/s, it takes some time :)

---

### Post by CharlesA on 2013-07-11
> **rubylaser said:**
> I will once I get it doing everything I want it to with all the unnecessary options ripped out.  It will probably be another week or so before I can release it, because to test the script, I need to let it run.  Even on the 160GB disk I'm running it on that can R/W around 120MB/s, it takes some time :)

Understandable. Looking forward to the end results.

---

### Post by CharlesA on 2013-07-14
Sorry to bump this thread, but I just created a 3 drive RAID 5 with mdadm and it is currently showing 1 as a spare...

```
mdadm - v3.2.5 - 18th May 2012
```
```
mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sd[bcd]1

```
```
root@Loki:~# cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4]
md0 : active (auto-read-only) raid5 sdd1[3](S) sdc1[1] sdb1[0]
      3906763776 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [UU_]

unused devices: <none>

```

```
root@Loki:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Sun Jul 14 16:36:40 2013
     Raid Level : raid5
     Array Size : 3906763776 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 1953381888 (1862.89 GiB 2000.26 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Sun Jul 14 16:36:40 2013
          State : clean, degraded
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

           Name : Loki:0  (local to host Loki)
           UUID : 7e33c05b:c1160a6a:fba6e791:5a1cae68
         Events : 0

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       0        0        2      removed

       3       8       49        -      spare   /dev/sdd1

```

Guess it's time to run SMART tests on all three drives, even though they completed badblocks fine.

EDIT: Maybe I am overracting.. I just created the array, so I think it's still syncing.

EDIT2: Nevermind, I forgot to format the array. Now it looks like it is rebuilding now. Recovery at 59000K/sec sounds about right (I guess?).

---

