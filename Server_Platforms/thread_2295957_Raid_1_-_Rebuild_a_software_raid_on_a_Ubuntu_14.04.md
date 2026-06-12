---
title: "Raid 1 - Rebuild a software raid on a Ubuntu 14.04.1 LTS Server"
date: 2015-09-22
forum: Server Platforms
---

### Post by green-tree on 2015-09-22
Hello Ubuntu forums and all who read it,

I am currently doing the administration of a Ubuntu 14 Server. It is a production server, that is why I am asking/requesting assistance, as I am doing that alone and have no experience with rebuilding an raid system.

So this is my situation:

On my server I use a software raid - raid 1. And one disk is now out of service. How do I know?
I receive emails saying: > [FONT=arial]A Fail event had been detected on md device /dev/md0.[/FONT][FONT=arial]or 
[/FONT]> [FONT=arial]A DegradedArray event had been detected on md device /dev/md2.[/FONT]

Well that made me curious so I used 2 common cli tools:

**mdadm -D** and **cat /proc/mdstat**

```
mdadm -D /dev/md0/:
        Version : 0.90
  Creation Time : Sat Feb  2 19:10:37 2013
     Raid Level : raid1
     Array Size : 1023936 (1000.11 MiB 1048.51 MB)
  Used Dev Size : 1023936 (1000.11 MiB 1048.51 MB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent


    Update Time : Tue Sep 22 18:39:02 2015
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 1
  Spare Devices : 0


           UUID : 667dbc4b:c42ae8af:3d186b3c:53958f34
         Events : 0.114


    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       0        0        1      removed


       2       8       17        -      faulty spare   /dev/sdb1
``````
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sda1[0] sdb1[2](F)
      1023936 blocks [2/1] [U_]


md3 : active raid1 sda6[0] sdb6[2](F)
      185151360 blocks [2/1] [U_]


md2 : active raid1 sdb5[2](F) sda5[0]
      277728192 blocks [2/1] [U_]


md1 : active raid1 sdb3[2](F) sda3[0]
      20479936 blocks [2/1] [U_]


unused devices: <none>
```




As you can see the complete sdb failed. So I tried to find out if it works. It shows up on /dev/

```
ls -l /dev/sd*
brw-rw---- 1 root disk 8,  0 Sep 22 18:23 /dev/sda
brw-rw---- 1 root disk 8,  1 Okt 11  2014 /dev/sda1
brw-rw---- 1 root disk 8,  2 Okt 11  2014 /dev/sda2
brw-rw---- 1 root disk 8,  3 Okt 11  2014 /dev/sda3
brw-rw---- 1 root disk 8,  4 Okt 11  2014 /dev/sda4
brw-rw---- 1 root disk 8,  5 Okt 11  2014 /dev/sda5
brw-rw---- 1 root disk 8,  6 Okt 11  2014 /dev/sda6
brw-rw---- 1 root disk 8, 16 Sep 22 18:22 /dev/sdb
brw-rw---- 1 root disk 8, 17 Okt 11  2014 /dev/sdb1
brw-rw---- 1 root disk 8, 18 Okt 11  2014 /dev/sdb2
brw-rw---- 1 root disk 8, 19 Okt 11  2014 /dev/sdb3
brw-rw---- 1 root disk 8, 20 Okt 11  2014 /dev/sdb4
brw-rw---- 1 root disk 8, 21 Okt 11  2014 /dev/sdb5
brw-rw---- 1 root disk 8, 22 Okt 11  2014 /dev/sdb6
```

But on **parted **only */dev/sda/* is listed:

```
(parted) print devices/dev/sda (500GB)
/dev/md1 (21,0GB)
/dev/md2 (284GB)
/dev/md3 (190GB)
/dev/md0 (1049MB)
```


I've read some posts on this forum so I hope that the following commands might help:

```
parted /dev/sda unit MiB print
Modell: ATA Hitachi HDS72105 (scsi)
Festplatte  /dev/sda:  476940MiB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: msdos


Nummer  Anfang     Ende       Größe      Typ       Dateisystem     Flags
 1      1,00MiB    1001MiB    1000MiB    primary   ext4            RAID
 2      1001MiB    4907MiB    3906MiB    primary   linux-swap(v1)
 3      4907MiB    24907MiB   20000MiB   primary   ext4            RAID
 4      24907MiB   476939MiB  452032MiB  extended                  LBA
 5      24908MiB   296127MiB  271219MiB  logical   ext4            RAID
 6      296127MiB  476939MiB  180812MiB  logical   ext4            RAID
```

I think the next step would be to remount sdb and sync the data/filesystem from sda to sdb and remount all /md[0123]/ devices. Is that correct?
I am wondering what I may have missed and what your recommendation might be for now?

Regards
Tree

---

### Post by darkod on 2015-09-22
If you use parted /dev/sda it will show only sda. Did you try something like:
```
parted /dev/sdb unit MiB print
```

Yes, the arrays are reported as degraded in /proc/mdstat but now it's important to see if sdb is completely failed or not. You can also use smartmontools to check the SMART data on sdb.

---

### Post by green-tree on 2015-09-22
**parted /dev/sdb unit MiB print** shows _no output_, but **smartctl **does:

```
smartctl /dev/sdb -a
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.2.0-51-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Vendor:               /1:0:0:0
Product:
User Capacity:        600.332.565.813.390.450 bytes [600 PB]
Logical block size:   774843950 bytes
Physical block size:  1583111168 bytes
Lowest aligned LBA:   8499
Logical block provisioning enabled, LBPRZ=0
>> Terminate command early due to bad response to IEC mode page
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
```

600 PB seems to be pretty much =D What happens here?
I thank you a lot for the assistance and the fast reply! Do we need to hurry or is the possibility for another drive-failure not so high?

Regards
Tree

---

### Post by darkod on 2015-09-22
It looks like the disk is gone. If you are willing to replace it it is always wise to act fast, although you have to have really bad luck for the other disk to fail soon too.

If you do decide to replace it, you have to remove the members from the arrays too. If you look at the -D output for md0 it says sdb1 is faulty but it is still listed there.

For each arrays and partition you will need to do something like:
```
mdadm /dev/md0 --remove /dev/sdb1
```

After that you replace the physical disk, install the new one, make the partitions as needed, and again for each array and partition do (I assume the new disk will be sdb again):
```
mdadm /dev/md0 --add /dev/sdb1
```

Example: [https://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array](https://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array)

---

### Post by green-tree on 2015-09-23
The server was rebooted and now sdb seems to be available. Even though the raid is still not working properly:

```
**parted /dev/sdb unit MiB print**Modell: ATA Hitachi HDS72105 (scsi)
Festplatte  /dev/sdb:  476940MiB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: msdos


Nummer  Anfang     Ende       Größe      Typ       Dateisystem     Flags
 1      1,00MiB    1001MiB    1000MiB    primary   ext4            RAID
 2      1001MiB    4907MiB    3906MiB    primary   linux-swap(v1)
 3      4907MiB    24907MiB   20000MiB   primary   ext4            RAID
 4      24907MiB   476939MiB  452032MiB  extended                  LBA
 5      24908MiB   296127MiB  271219MiB  logical   ext4            RAID
 6      296127MiB  476939MiB  180812MiB  logical   ext4            RAID
``````
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md2 : active raid1 sda5[0]
      277728192 blocks [2/1] [U_]


md1 : active raid1 sda3[0]
      20479936 blocks [2/1] [U_]


md0 : active raid1 sda1[0]
      1023936 blocks [2/1] [U_]


md3 : active raid1 sda6[0]
      185151360 blocks [2/1] [U_]


unused devices: <none>
``````
smartctl -a /dev/sdb
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-37-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Hitachi Deskstar 7K1000.C
Device Model:     Hitachi HDS721050CLA362
Serial Number:    JP5530HK1J8PPP
LU WWN Device Id: 5 000cca 377d57e19
Firmware Version: JP2OA3MA
User Capacity:    500.107.862.016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Wed Sep 23 07:35:26 2015 CEST
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
data collection:                ( 4798) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        (  80) minutes.
SCT capabilities:              (0x003d) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   135   135   054    Pre-fail  Offline      -       98
  3 Spin_Up_Time            0x0007   117   117   024    Pre-fail  Always       -       195 (Average 195)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       20
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   132   132   020    Pre-fail  Offline      -       34
  9 Power_On_Hours          0x0012   095   095   000    Old_age   Always       -       40503
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       20
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       44
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       44
194 Temperature_Celsius     0x0002   222   222   000    Old_age   Always       -       27 (Min/Max 19/42)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       62


SMART Error Log Version: 0
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     40496         -
# 2  Short offline       Aborted by host               90%     40495         -
# 3  Extended offline    Completed without error       00%       198         -
# 4  Short offline       Completed without error       00%       146         -


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

The drive seems to be back in service. I don't know if the smart stats are a bad or a good sign. Do I need to wipe the drive before bringing it back to the raid? I mean now it is out of sync.

---

### Post by darkod on 2015-09-23
No, don't wipe it. It will have more to sync. Because it was already a member of your raid you should be able to simply --re-add the partitions to the relevant md devices. It should sync the missing data and that's it. Providing the disk is really good.

You can start with the md device of least importance first. I don't know which one is that so I will just give you example with md0.
```
sudo mdadm /dev/md0 --re-add /dev/sdb1
```

See if it accepts the command or if it gives an error. If it accepts it, you can check with cat /proc/mdstat if it is syncing OK.

PS. Depending when and how the partitions failed from the arrays, they might not like the --re-add command. In that case try with --add as next step and see if it accepts that.

---

### Post by green-tree on 2015-09-23
[SIZE=2][FONT=arial]I tried to use --re-add on md0

**mdadm /dev/md0 --re-add /dev/sdb1**

Nothing happened. So I followed your next suggestion to use --add which worked.

[/FONT][/SIZE][SIZE=2][FONT=arial]**mdadm /dev/md0 --add /dev/sdb1**[/FONT][/SIZE]
[SIZE=2][FONT=arial]**mdadm: added /dev/sdb1**[/FONT][/SIZE]
[SIZE=2][FONT=arial]
Now checked if all devices are up and yes: On md0 it showed [UU].[/FONT][/SIZE]
[FONT=arial][/FONT][SIZE=3][/SIZE][SIZE=2][FONT=arial]After that I checked the consistency, which also does an auto-sync if something is bad:
**/usr/share/mdadm/checkarray /dev/md0**

At first it synced but at the progress of ~5% it just stopped and _**sdb is gone again (completely).**_ Faulty array and not listed in [/FONT][/SIZE][FONT=Verdana]lsblk. [/FONT][FONT=arial]Can I find out what made the device disappear again?[/FONT][SIZE=2][FONT=arial]
Regards
Tree[/FONT][/SIZE]

---

### Post by darkod on 2015-09-23
If the disk went missing again as soon as you tried to use it, that is definitely not a good sign. In fact it reminds me of a disk I tried to save/investigate once. With much effort you could make it to show and as soon as you try to write to it, it went missing again. No matter what I tried, it never started working.

For a production server I would say don't count on that disk any more. Get a new one ASAP, make the same partitions and add them to your arrays. Let it sync and you will have a piece of mind with the arrays being a full mirror again.

After that if you want to play with the faulty disk, you can do it as much as you want and as long as you want... :)

---

### Post by green-tree on 2015-10-19
Hello darkod,

thank you a lot for the assistance. I completely changed the server (including the hardware/hdd). So the problem is gone now.

Best wishes
tree

---

