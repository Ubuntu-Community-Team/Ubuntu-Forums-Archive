---
title: "mdadm RAID0 very slow read speeds"
date: 2013-08-10
forum: Server Platforms
---

### Post by hansamurai on 2013-08-10
Hi, I'm switching over from FreeNAS to Ubuntu Server 12.04 for my NAS box and am converting my ZFS pools to mdadm RAIDs and am having some serious issues reading/streaming files over SMB.

Server is AMD E-350 APU with 8GB DDR3 RAM.

I have two 1.5TB hard drives of different makes in a RAID0 configuration, and then shared over the network using samba.

Individually, one drive would copy over SMB to my desktop at 100 MB/s, the other at around 70 MB/s. (the first is a Seagate ST1500DL003 5900 RPM drive and the second is a WD Green WD15EADS with a few more hours under its belt.)

**When striped together, I get a MAX of 10 MB/s** under the same network conditions. When ssh'd into the server browsing the drive simply doesn't feel snappy either. Totally different than my old ZFS stripe which worked fine.

Here's what I used to create the RAID and create the file system:

```
parted -a optimal /dev/sdb
    mkpart primary 1MiB 100%
    set 1 raid on
    quit
parted -a optimal /dev/sdc
    mkpart primary 1MiB 100%
    set 1 raid on
    quit
mdadm --create --verbose /dev/md0 --level=stripe --chunk=32 --raid-devices=2 /dev/sdb1 /dev/sdb2
mkfs.ext4 -b 4096 -E stride=8,stripe-width=16 /dev/md0
tune2fs -O has_journal -o journal_data_writeback /dev/md0
tune2fs -O dir_index /dev/md0
e2fsck -D /dev/md0
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
mount /dev/md0 /mnt/storage -o noatime,nodiratime,data=writeback,stripe=16,barrier=0,errors=remount-ro
```

I understand some of my file system options may be risky, but I tried it yesterday with the defaults (didn't specify chunk, stride, stripe-width; no journal tuning) and got the same result.

I also know that I will lose the stripe if I lose one drive, I understand that, I have nightly backups running.

Here's some more information:

```
#cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid0 sdb1[0] sdc1[1]
      2930274240 blocks super 1.2 32k chunks
      
unused devices: <none>

```
```
#mdadm -D /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Sat Aug 10 16:20:23 2013
     Raid Level : raid0
     Array Size : 2930274240 (2794.53 GiB 3000.60 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Sat Aug 10 16:20:23 2013
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 32K

           Name : oldtown:0  (local to host oldtown)
           UUID : e50ae570:427d0db7:475bc4cc:8f86f703
         Events : 0

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1

```
```
#hdparm -tT /dev/md0
/dev/md0:
 Timing cached reads:   2122 MB in  2.00 seconds = 1060.41 MB/sec
 Timing buffered disk reads: 302 MB in  4.59 seconds =  65.80 MB/sec
```
```
#dd if=/dev/zero of=testfile bs=1M count=5000
5000+0 records in
5000+0 records out
5242880000 bytes (5.2 GB) copied, 65.2134 s, 80.4 MB/s

#dd if=testfile of=/dev/zero bs=1M
5+0 records in
5+0 records out
5242880000 bytes (5.2 GB) copied, 4.0535 s, 1.3 GB/s

#dd if=/dev/zero of=testfile bs=1000M count=5
5+0 records in
5+0 records out
5242880000 bytes (5.2 GB) copied, 65.4636 s, 80.1 MB/s

#dd if=testfile of=/dev/zero bs=1000M
5+0 records in
5+0 records out
5242880000 bytes (5.2 GB) copied, 5.69963 s, 920 MB/s
```
```
#time cp testfile testfile2
real 2m42.178s
user 0m0.100s
sys 0m19.525
```

Excerpt from smb.conf
```
[storage]
comment=
path=/mnt/storage
guest ok=yes
browseable=yes
create mask=0744
directory mask=0755
read only=no
follow symlinks=yes
wide links=no
```

[IMG]http://i.imgur.com/6Ni9fJe.png[/IMG]

Thanks in advance for your help!

Also for what it's worth, the 3TB drive is running UFS right now and when samba shared transfers at a speedy 100 MB/s.

---

### Post by rubylaser on 2013-08-11
This whole setup is risky, not just the filesystem :)  Why did you move from ZFS, a VERY reliable filesystem, to a RAID0?  I'm sure you know the downside of losing a disk in RAID0, so I'll move on, but I'd at least consider adding some parity (mdadm RAID5/6, ZFS, or [SnapRAID]("http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04") (this is great for home media storage).  Prehaps you have a backup system in place, or you don't mind the process of 3TB of data in the event of a failed disk.
 
I'd like to see the results of a few more tests before rendering a judgement.  You have 8GB of RAM in your system, so a 5GB dd test is really hitting the cache, can you try with a larger test on each disk, like this?

```

dd if=/dev/zero of=/dev/sdX_mountpoint/testfile bs=1M count=20000
sync
dd if=/dev/sdX_mountpoint/testfile of=/dev/null bs=1M

```

Also, could we see the SMART data on each disk?
```

apt-get install smartmontools
smarctl -a /dev/sdX

```

---

### Post by hansamurai on 2013-08-11
This is just one aspect of my NAS setup, hopefully we can figure this out! Thanks for your help.

```
#dd if=/dev/zero of=/testfile bs=1M count=20000
20000+0 records in
20000+0 records out
20971520000 bytes (21 GB) copied, 569.694 s, 36.8 MB/s

#sync

#dd if=testfile of=/dev/null bs=1M
20000+0 records in
20000+0 records out
20971520000 bytes (21 GB) copied, 202.878 s, 103 MB/s
```

```
#smartctl -a /dev/sdb
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-23-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green
Device Model:     WDC WD15EADS-00P8B0
Serial Number:    WD-WMAVU0513688
LU WWN Device Id: 5 0014ee 001a35966
Firmware Version: 01.00A01
User Capacity:    1,500,301,910,016 bytes [1.50 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Aug 11 09:35:31 2013 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)	Offline data collection activity
					was suspended by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(34500) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 255) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   183   182   021    Pre-fail  Always       -       5850
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       346
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   063   063   000    Old_age   Always       -       27319
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       226
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       201
193 Load_Cycle_Count        0x0032   181   181   000    Old_age   Always       -       59116
194 Temperature_Celsius     0x0022   119   102   000    Old_age   Always       -       31
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       55
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     27299         -
# 2  Short offline       Completed without error       00%      9568         -
# 3  Short offline       Completed without error       00%      9530         -

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

```
#smartctl -a /dev/sdc
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-23-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda Green (Adv. Format)
Device Model:     ST1500DL003-9VT16L
Serial Number:    5YD3YPT3
LU WWN Device Id: 5 000c50 038b2f6ca
Firmware Version: CC32
User Capacity:    1,500,301,910,016 bytes [1.50 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Sun Aug 11 09:35:41 2013 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(  633) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 255) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x30b7)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   116   099   006    Pre-fail  Always       -       107905120
  3 Spin_Up_Time            0x0003   093   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       46
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   070   060   030    Pre-fail  Always       -       11675183
  9 Power_On_Hours          0x0032   083   083   000    Old_age   Always       -       15074
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       46
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   069   060   045    Old_age   Always       -       31 (Min/Max 30/33)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       24
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       46
194 Temperature_Celsius     0x0022   031   040   000    Old_age   Always       -       31 (0 21 0 0)
195 Hardware_ECC_Recovered  0x001a   023   006   000    Old_age   Always       -       107905120
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       231193794591460
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       3680774141
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       248709897

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     15055         -

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

