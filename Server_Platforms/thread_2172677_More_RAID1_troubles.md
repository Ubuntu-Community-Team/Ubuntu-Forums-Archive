---
title: "More RAID1 troubles"
date: 2013-09-06
forum: Server Platforms
---

### Post by soapdude on 2013-09-06
I thought everything was going well with my RAID1 rebuild. I had a failed RAID1 setup, and with help from this forum, I purchased a third hard drive, copied data to that drive, and rebuilt the RAID1 array. The computer boots fine, and there don't seem to be any problems, but when I look cat /proc/mdstat: 

The part I'm concerned about is the [_U] after md1.. Is this normal?

```
md1 : active raid1 sda2[1]      1949965120 blocks super 1.2 [2/1] [_U]
      
md0 : active raid1 sda1[1] sdc1[2]
      3414976 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>

```

examines:

```
mdadm --examine /dev/sda1/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 5603467b:9c5dcb9d:e3ae857c:beff72f6
           Name : server:0  (local to host server)
  Creation Time : Mon Nov  5 13:58:10 2012
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 6830080 (3.26 GiB 3.50 GB)
     Array Size : 3414976 (3.26 GiB 3.50 GB)
  Used Dev Size : 6829952 (3.26 GiB 3.50 GB)
    Data Offset : 4096 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 4b36d6a3:82546dba:1a1abcc8:63bf9134


    Update Time : Fri Sep  6 12:53:09 2013
       Checksum : 3c3b3d95 - correct
         Events : 2168




   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing)

```


```
mdadm --examine /dev/sda2/dev/sda2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : b7194b1f:398f8f86:c7bf4b30:88fcf85f
           Name : server:1  (local to host server)
  Creation Time : Mon Nov  5 13:58:28 2012
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 3899930624 (1859.63 GiB 1996.76 GB)
     Array Size : 1949965120 (1859.63 GiB 1996.76 GB)
  Used Dev Size : 3899930240 (1859.63 GiB 1996.76 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 25751207:3134b635:d41c0cff:a9a8a152


    Update Time : Fri Sep  6 13:14:06 2013
       Checksum : ea55d935 - correct
         Events : 217067




   Device Role : Active device 1
   Array State : .A ('A' == active, '.' == missing)



```

```
mdadm --examine /dev/sdc1/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 5603467b:9c5dcb9d:e3ae857c:beff72f6
           Name : server:0  (local to host server)
  Creation Time : Mon Nov  5 13:58:10 2012
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 6830080 (3.26 GiB 3.50 GB)
     Array Size : 3414976 (3.26 GiB 3.50 GB)
  Used Dev Size : 6829952 (3.26 GiB 3.50 GB)
    Data Offset : 4096 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 55cab61a:9c5b5305:448bf359:41cc9abc


    Update Time : Fri Sep  6 12:53:09 2013
       Checksum : 174256c1 - correct
         Events : 2168




   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing)



```
```

mdadm --examine /dev/sdc2
/dev/sdc2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : b7194b1f:398f8f86:c7bf4b30:88fcf85f
           Name : server:1  (local to host server)
  Creation Time : Mon Nov  5 13:58:28 2012
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 3899930624 (1859.63 GiB 1996.76 GB)
     Array Size : 1949965120 (1859.63 GiB 1996.76 GB)
  Used Dev Size : 3899930240 (1859.63 GiB 1996.76 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 3aec1dd9:5b585c3c:fb6d8560:48c67af1


    Update Time : Tue Sep  3 16:56:41 2013
       Checksum : c35431d9 - correct
         Events : 155355




   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing)

```




Sorry to keep having problems. :/ How can I move forward? Thank you!

---

### Post by soapdude on 2013-09-06
Ok, so I'm going to use dd to copy the data to a third disk again.. (sdb)

then this:

```

mdadm --zero-superblock /dev/sda1
mdadm --zero-superblock /dev/sda1



mdadm --manage /dev/md0 --add /dev/sdb1
mdadm --manage /dev/md1 --add /dev/sdb2
```

Will this work?

---

### Post by SaturnusDJ on 2013-09-06
```
[_U]
```
Means array with 2 members, 1 member missing. Not something you want.

I don't understand what you are trying with the last set of commands. Maybe you copied it from the other thread without editing?
From the other thread I remember you're keeping /dev/sdb aside to be fail safe.

Add /dev/sdc2 back to /dev/md1. Don't use /dev/sdc2 for anything else (it's data is 3 days outdated). Unless that is exactly what you want.
Does the disk keep dropping? Then maybe something is wrong with your hardware.

---

### Post by soapdude on 2013-09-06
I'm sorry, but I feel super lost here. I thought everything was working fine, and the system boots without an error message... Here's what I've done now. I used sfdisk to copy sda to sdb, and I've added sdb to the array. This is happening now:

```
cat /proc/mdstatPersonalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdb2[2] sda2[1]
      1949965120 blocks super 1.2 [2/1] [_U]
      	resync=DELAYED
      
md0 : active raid1 sdb1[3] sda1[1] sdc1[2](F)
      3414976 blocks super 1.2 [2/1] [_U]
      [>....................]  recovery =  1.1% (39296/3414976) finish=32.9min speed=1708K/sec
      
unused devices: <none>

```

Can I remove sdc1 from md0 somehow..? Thank you so much for your patience with me!

---

### Post by SaturnusDJ on 2013-09-06
No problem.

Is this 'sdb' the same sdb as in the previous thread? Then you don't have a working copy of the data right now unless sdc is okay.

```
mdadm /dev/md0 --remove /dev/sdc1
```

---

### Post by soapdude on 2013-09-06
Yes, I believe sdc is ok. Either way, I can lose a few days worth of data without problem (It was sfdisk'ed when I rebuilt the array in the first place)

---

### Post by SaturnusDJ on 2013-09-06
Raid 1 members can be mounted like non raid disks.

---

### Post by soapdude on 2013-09-07
I'm resyncing now, but it's running at less than 500kbps and they're 2Tb drives. 

```
cat /proc/sys/dev/raid/speed_limit_min50000

```

```

cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sdb2[2] sda2[1]
      1949965120 blocks super 1.2 [2/1] [_U]
      [>....................]  recovery =  2.7% (54185408/1949965120) finish=90823.8min speed=347K/sec


md0 : active raid1 sdb1[3] sda1[1]
      3414976 blocks super 1.2 [2/2] [UU]


unused devices: <none>

```

Is there anything I can do to make this quicker? I am currently the only one logged onto the server.

---

### Post by SaturnusDJ on 2013-09-07
Yes: [http://www.cyberciti.biz/tips/linux-raid-increase-resync-rebuild-speed.html](http://www.cyberciti.biz/tips/linux-raid-increase-resync-rebuild-speed.html)

If it doesn't work it's time to in-depth look at S.M.A.R.T. and other hardware aspects.

---

### Post by soapdude on 2013-09-07
Ok, so it appears the changes I make to ```
cat /proc/sys/dev/raid/speed_limit_max
``` and ```
cat /proc/sys/dev/raid/speed_limit_min
``` aren't instant? Do I need to restart the sync for them to take effect during sync? To test, I've set max to 0, and I'm still getting ```
cat /proc/mdstatPersonalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sdb2[2] sda2[1]
      1949965120 blocks super 1.2 [2/1] [_U]
      [>....................]  recovery =  3.1% (61106112/1949965120) finish=79544.6min speed=395K/sec


md0 : active raid1 sdb1[3] sda1[1]
      3414976 blocks super 1.2 [2/2] [UU]


unused devices: <none>

``` several minutes later.

---

### Post by soapdude on 2013-09-07
Also, some of the other things I can't do because there is an active sync happening..?

---

### Post by SaturnusDJ on 2013-09-07
Try this:
```

hdparm -tT /dev/sd[a,b]

```
Quick read test of hard disks.

Also post the outcome of this:
```

smartctl -a /dev/sda
smartctl -a /dev/sdb

```

---

### Post by soapdude on 2013-09-07
```

:/home# hdparm -tT /dev/sda


/dev/sda:
 Timing cached reads:     2 MB in  3.49 seconds = 586.97 kB/sec
 Timing buffered disk reads:   2 MB in  3.37 seconds = 607.75 kB/sec
root@server:/home# hdparm -tT /dev/sdb


/dev/sdb:
 Timing cached reads:     2 MB in  2.69 seconds = 761.68 kB/sec
 Timing buffered disk reads:   4 MB in  3.17 seconds =   1.26 MB/sec
root@server:/home# smartctl -a /dev/sda
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-29-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EARX-00PASB0
Serial Number:    WD-WCAZAD561584
LU WWN Device Id: 5 0014ee 25bd353c4
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Sep  7 22:25:39 2013 PHT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x84) Offline data collection activity
                                        was suspended by an interrupting command from host.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (36480) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x3035) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   176   164   021    Pre-fail  Always       -       6191
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       52
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   091   091   000    Old_age   Always       -       6935
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       51
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       36
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       818675
194 Temperature_Celsius     0x0022   106   101   000    Old_age   Always       -       44
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      6618         -
# 2  Short offline       Aborted by host               40%      6618         -


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


root@server:/home# smartctl -a /dev/sdb
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-29-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EZRX-00D8PB0
Serial Number:    WD-WMC4N0116506
LU WWN Device Id: 5 0014ee 603a56c05
Firmware Version: 80.00A80
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   9
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Sep  7 22:25:59 2013 PHT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x80) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (25920) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x7035) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   100   253   021    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       3
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       106
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       3
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       0
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       29
194 Temperature_Celsius     0x0022   109   108   000    Old_age   Always       -       41
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]




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

---

### Post by SaturnusDJ on 2013-09-07
Okay the speeds are total ****.

/dev/sda has an enormous LCC (Load_Cycle_Count), meaning it parked the disk heads that many times. For servers it's most times best to disable (quick) head parks.

You have to really make sure the data you're working with is safely backed up.

Now back to the low speeds...is something I/O going on? Maybe it's the controller because the (new?) disk /dev/sdb is affected too.

---

### Post by soapdude on 2013-09-07
For the head parking, should I run something like this? Is it safe to run this during sync?

```

[COLOR=#333333][FONT=Ubuntu Mono]hdparm -B 128 /dev/sda

```

What about fact that this has no affect on the sync:

```
[/FONT][/COLOR]echo 0 > /proc/sys/dev/raid/speed_limit_max
```

---

### Post by soapdude on 2013-09-07
Also, can I stop this sync, copy the data to the two new drives, and try from there?

---

### Post by SaturnusDJ on 2013-09-07
That hdparm command should work, only now is not the good moment. In theory it shouldn't do any harm...but you know...

I think 0 isn't allowed.

I suggest you have the data backed-up, then have a look why the transfer rates are that slow. So yes, that means stopping the sync. Failing the drive that's being synced should stop the sync.

---

### Post by soapdude on 2013-09-07
I tried 15, and it's still not working..?

```

 echo 15 > /proc/sys/dev/raid/speed_limit_max

```
```
cat /proc/mdstatPersonalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sdb2[2] sda2[1]
      1949965120 blocks super 1.2 [2/1] [_U]
      [>....................]  recovery =  4.2% (83166272/1949965120) finish=107520.3min speed=288K/sec


md0 : active raid1 sdb1[3] sda1[1]
      3414976 blocks super 1.2 [2/2] [UU]


unused devices: <none>

```

And I can fail the drive like this:
```
[COLOR=#000000][FONT=Courier New][I]mdadm --manage /dev/md1 --fail /dev/sdb2
```

during sync without trouble?[/I][/FONT][/COLOR]

---

### Post by soapdude on 2013-09-08
Ok, so I have successfully failed the second drive. Now I want to backup the original drive to a third drive. My problem is that while sda will boot fine with no other drives installed, as soon as I install a second drive in the computer, it won't boot. If I replace it with the original sdb drive, it boots fine... What is going on here?

---

### Post by soapdude on 2013-09-09
I was able to boot from a live CD and reinstall GRUB on sda. Next, I installed a new drive alongside the old sda drive. I ensured that the superblocks were zeroed on sdb, and I followed the post about speeding up RAID1 sync. I copied partition tables to sdb from sda using sfdisk, and then restarted the sync. It has now been running perfectly at around 30Mbps for an hour. Thank you for all of your help. If everything works out ok, I'll update this post and mark it solved!

---

