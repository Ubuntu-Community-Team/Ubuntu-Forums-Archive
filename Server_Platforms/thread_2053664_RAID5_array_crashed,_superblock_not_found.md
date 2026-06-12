---
title: "RAID5 array crashed, superblock not found"
date: 2012-09-05
forum: Server Platforms
---

### Post by Rustafur on 2012-09-05
Came home from work to a crashed RAID5 array in my 10.04 box.

I went into Disk Utility and stopped the array, and when I tried to restart the array I received this error:  

Error assembling array: mdadm exited with exit code 1: mdadm: metadata format 00.90 unknown, ignored.
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: /dev/sdc1 has no superblock - assembly aborted


So I ran mdadm -D on my raid array, and got this as a result

```
root@server:/home/administrator# mdadm -D /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Wed Jun 30 21:40:10 2010
     Raid Level : raid5
  Used Dev Size : 625129216 (596.17 GiB 640.13 GB)
   Raid Devices : 4
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Sep  5 16:41:12 2012
          State : active, degraded, Not Started
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 286f028d:5d5ee152:01f9e43d:ac30fbff
         Events : 0.67498

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       0        0        1      removed
       2       0        0        2      removed
       3       8       33        3      active sync   /dev/sdc1
```

Immediately I noticed the Raid Devices : 4, Total Devices : 2 and my heart just sank straight into my chair.  I can find all 4 drives in GParted, and also the disk utility, and I can even run diagnostics on each of the 4 drives in my array.  Is this what I think it means, that 2 of the 4 drives suddenly gave up the ghost and so my array is toast?  

Please let me know if you need any further information, I'm not entirely sure what to look for, in the way of useful information.  Thanks!!!

---

### Post by rubylaser on 2012-09-06
Can you give me the output of these (I'm assuming the disks that should be in your array are sdb,sdc,sdd,sde please change the values below if that's not the case?

```
cat /etc/mdadm/mdadm.conf
```
```
mdadm -E /dev/sd[bcde]1
```
```
smartctl -a /dev/sdb
```
```
smartctl -a /dev/sdc
```
```
smartctl -a /dev/sdd
```
```
smartctl -a /dev/sde
```

---

### Post by Rustafur on 2012-09-06
Yes, I'll run these as soon as I get a chance tonight, thanks in advance!

---

### Post by Rustafur on 2012-09-06
Here's the results of what you asked for.  And, yes you were correct about the sd[bcde] values.  Sorry for the delay in getting this info to you, life's busy at the moment :)

**cat /etc/mdadm/mdadm.conf**
```
root@server:/home/administrator# cat /etc/mdadm/mdadm.conf
DEVICE partitions
ARRAY /dev/md0 level=raid5 num-devices=3 metadata=00.90 UUID=286f028d:5d5ee152:01f9e43d:ac30fbff
MAILADDR myemailaddress@yeahbuddy.com
```

**mdadm -E /dev/sd[bcde]1**
```
root@server:/home/administrator# mdadm -E /dev/sd[bcde]1
mdadm: metadata format 00.90 unknown, ignored.
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 286f028d:5d5ee152:01f9e43d:ac30fbff
  Creation Time : Wed Jun 30 21:40:10 2010
     Raid Level : raid5
  Used Dev Size : 625129216 (596.17 GiB 640.13 GB)
     Array Size : 1875387648 (1788.51 GiB 1920.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed Sep  5 16:41:12 2012
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 9edda200 - correct
         Events : 67498

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       0        0        1      faulty removed
   2     2       0        0        2      faulty removed
   3     3       8       33        3      active sync   /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 286f028d:5d5ee152:01f9e43d:ac30fbff
  Creation Time : Wed Jun 30 21:40:10 2010
     Raid Level : raid5
  Used Dev Size : 625129216 (596.17 GiB 640.13 GB)
     Array Size : 1875387648 (1788.51 GiB 1920.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed Sep  5 16:41:12 2012
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 9edda216 - correct
         Events : 67498

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       33        3      active sync   /dev/sdc1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       0        0        1      faulty removed
   2     2       0        0        2      faulty removed
   3     3       8       33        3      active sync   /dev/sdc1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 286f028d:5d5ee152:01f9e43d:ac30fbff
  Creation Time : Wed Jun 30 21:40:10 2010
     Raid Level : raid5
  Used Dev Size : 625129216 (596.17 GiB 640.13 GB)
     Array Size : 1875387648 (1788.51 GiB 1920.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Aug 31 09:26:13 2012
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 9ed5937b - correct
         Events : 65081

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       49        1      active sync   /dev/sdd1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       8       65        2      active sync   /dev/sde1
   3     3       8       33        3      active sync   /dev/sdc1
/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 286f028d:5d5ee152:01f9e43d:ac30fbff
  Creation Time : Wed Jun 30 21:40:10 2010
     Raid Level : raid5
  Used Dev Size : 625129216 (596.17 GiB 640.13 GB)
     Array Size : 1875387648 (1788.51 GiB 1920.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed Sep  5 05:49:53 2012
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 9edd0958 - correct
         Events : 67478

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       65        2      active sync   /dev/sde1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       0        0        1      faulty removed
   2     2       8       65        2      active sync   /dev/sde1
   3     3       8       33        3      active sync   /dev/sdc1
```

**smartctl -a /dev/sdb**
```
root@server:/home/administrator# smartctl -a /dev/sdb
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     ST3640323AS
Serial Number:    9VK0H37J
Firmware Version: CC1F
User Capacity:    640,135,028,736 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Thu Sep  6 18:26:40 2012 CDT
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
data collection: 		 ( 617) seconds.
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
recommended polling time: 	 ( 130) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x103f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   116   099   006    Pre-fail  Always       -       101796718
  3 Spin_Up_Time            0x0003   100   100   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       62
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       1
  7 Seek_Error_Rate         0x000f   080   060   030    Pre-fail  Always       -       107072640
  9 Power_On_Hours          0x0032   066   066   000    Old_age   Always       -       29909
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       62
184 Unknown_Attribute       0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   041   041   000    Old_age   Always       -       59
190 Airflow_Temperature_Cel 0x0022   073   047   045    Old_age   Always       -       27 (Lifetime Min/Max 27/33)
194 Temperature_Celsius     0x0022   027   053   000    Old_age   Always       -       27 (0 16 0 0)
195 Hardware_ECC_Recovered  0x001a   039   027   000    Old_age   Always       -       101796718
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       173993420157843
241 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       3378556904
242 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       2639821366

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

**smartctl -a /dev/sdc**
```
root@server:/home/administrator# smartctl -a /dev/sdc
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD6401AALS-00J7B0
Serial Number:    WD-WMATV7390306
Firmware Version: 05.00K05
User Capacity:    640,135,028,736 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Sep  6 18:27:30 2012 CDT
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
data collection: 		 (12780) seconds.
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
recommended polling time: 	 ( 149) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x3037)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   221   221   021    Pre-fail  Always       -       8916
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       54
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   074   074   000    Old_age   Always       -       19028
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       46
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       33
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       54
194 Temperature_Celsius     0x0022   116   107   000    Old_age   Always       -       34
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     19005         -

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

**smartctl -a /dev/sdd**
```
root@server:/home/administrator# smartctl -a /dev/sdd
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     ST3640323AS
Serial Number:    9VK0HBE3
Firmware Version: CC1F
User Capacity:    640,135,028,736 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Thu Sep  6 18:28:09 2012 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 617) seconds.
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
recommended polling time: 	 ( 135) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x103f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   118   099   006    Pre-fail  Always       -       176166579
  3 Spin_Up_Time            0x0003   100   100   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       64
  5 Reallocated_Sector_Ct   0x0033   001   001   036    Pre-fail  Always   FAILING_NOW 4095
  7 Seek_Error_Rate         0x000f   079   060   030    Pre-fail  Always       -       89504054
  9 Power_On_Hours          0x0032   066   066   000    Old_age   Always       -       29921
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   037   020    Old_age   Always       -       64
184 Unknown_Attribute       0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   071   071   000    Old_age   Always       -       29
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   001   001   000    Old_age   Always       -       120
190 Airflow_Temperature_Cel 0x0022   071   047   045    Old_age   Always       -       29 (Lifetime Min/Max 29/35)
194 Temperature_Celsius     0x0022   029   053   000    Old_age   Always       -       29 (0 15 0 0)
195 Hardware_ECC_Recovered  0x001a   047   027   000    Old_age   Always       -       176166579
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       69681549440224
241 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       3409315448
242 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       729545650

SMART Error Log Version: 1
ATA Error Count: 42 (device log contains only the most recent five errors)
	CR = Command Register [HEX]
	FR = Features Register [HEX]
	SC = Sector Count Register [HEX]
	SN = Sector Number Register [HEX]
	CL = Cylinder Low Register [HEX]
	CH = Cylinder High Register [HEX]
	DH = Device/Head Register [HEX]
	DC = Device Command Register [HEX]
	ER = Error register [HEX]
	ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 42 occurred at disk power-on lifetime: 29896 hours (1245 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 e0  Device Fault; Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  a1 00 00 00 00 00 a0 00  38d+00:54:23.081  IDENTIFY PACKET DEVICE
  ec 00 00 00 00 00 a0 00  38d+00:54:23.081  IDENTIFY DEVICE
  ff 00 00 00 00 00 00 00  38d+00:54:22.351  [VENDOR SPECIFIC]
  00 00 00 00 00 00 00 ff  38d+00:54:22.351  NOP [Abort queued commands]
  ff 00 00 00 00 00 00 00  38d+00:54:19.838  [VENDOR SPECIFIC]

Error 41 occurred at disk power-on lifetime: 29896 hours (1245 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 e0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 00  38d+00:54:23.081  IDENTIFY DEVICE
  ff 00 00 00 00 00 00 00  38d+00:54:22.351  [VENDOR SPECIFIC]
  00 00 00 00 00 00 00 ff  38d+00:54:22.351  NOP [Abort queued commands]
  ff 00 00 00 00 00 00 00  38d+00:54:19.838  [VENDOR SPECIFIC]
  00 00 00 00 00 00 00 ff  38d+00:54:19.838  NOP [Abort queued commands]

Error 40 occurred at disk power-on lifetime: 29896 hours (1245 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 e0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 01 00 00 00 a0 00  38d+00:54:11.889  IDENTIFY DEVICE
  ff 00 00 00 00 00 00 00  38d+00:54:11.851  [VENDOR SPECIFIC]
  00 00 00 00 00 00 00 ff  38d+00:54:11.851  NOP [Abort queued commands]
  ff 00 00 00 00 00 00 00  38d+00:54:08.981  [VENDOR SPECIFIC]
  00 00 00 00 00 00 00 ff  38d+00:54:08.980  NOP [Abort queued commands]

Error 39 occurred at disk power-on lifetime: 29768 hours (1240 days + 8 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 e0  Device Fault; Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  a1 00 00 00 00 00 a0 00  32d+16:36:55.399  IDENTIFY PACKET DEVICE
  ec 00 00 00 00 00 a0 00  32d+16:36:55.398  IDENTIFY DEVICE
  ff 00 00 00 00 00 00 00  32d+16:36:55.068  [VENDOR SPECIFIC]
  00 00 00 00 00 00 00 ff  32d+16:36:55.068  NOP [Abort queued commands]
  a1 00 00 00 00 00 a0 00  32d+16:36:50.048  IDENTIFY PACKET DEVICE

Error 38 occurred at disk power-on lifetime: 29768 hours (1240 days + 8 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 e0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 00  32d+16:36:55.398  IDENTIFY DEVICE
  ff 00 00 00 00 00 00 00  32d+16:36:55.068  [VENDOR SPECIFIC]
  00 00 00 00 00 00 00 ff  32d+16:36:55.068  NOP [Abort queued commands]
  a1 00 00 00 00 00 a0 00  32d+16:36:50.048  IDENTIFY PACKET DEVICE
  ec 00 00 00 00 00 a0 00  32d+16:36:50.048  IDENTIFY DEVICE

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

**smartctl -a /dev/sde**
```
root@server:/home/administrator# smartctl -a /dev/sde
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     ST3640323AS
Serial Number:    9VK0HBN1
Firmware Version: CC1F
User Capacity:    640,135,028,736 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Thu Sep  6 18:28:45 2012 CDT
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
data collection: 		 ( 617) seconds.
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
recommended polling time: 	 ( 132) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x103f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   101   099   006    Pre-fail  Always       -       33507330
  3 Spin_Up_Time            0x0003   100   100   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       59
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       1
  7 Seek_Error_Rate         0x000f   080   060   030    Pre-fail  Always       -       103215642
  9 Power_On_Hours          0x0032   066   066   000    Old_age   Always       -       29928
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       60
184 Unknown_Attribute       0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   089   089   000    Old_age   Always       -       11
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   022   022   000    Old_age   Always       -       78
190 Airflow_Temperature_Cel 0x0022   070   048   045    Old_age   Always       -       30 (Lifetime Min/Max 30/34)
194 Temperature_Celsius     0x0022   030   052   000    Old_age   Always       -       30 (0 15 0 0)
195 Hardware_ECC_Recovered  0x001a   037   029   000    Old_age   Always       -       33507330
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       68
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       68
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       58372900549863
241 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       4052766202
242 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       3342753829

SMART Error Log Version: 1
ATA Error Count: 7 (device log contains only the most recent five errors)
	CR = Command Register [HEX]
	FR = Features Register [HEX]
	SC = Sector Count Register [HEX]
	SN = Sector Number Register [HEX]
	CL = Cylinder Low Register [HEX]
	CH = Cylinder High Register [HEX]
	DH = Device/Head Register [HEX]
	DC = Device Command Register [HEX]
	ER = Error register [HEX]
	ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 7 occurred at disk power-on lifetime: 29892 hours (1245 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 80 ff ff ff 4f 00  24d+15:28:48.990  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00  24d+15:28:48.962  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00  24d+15:28:48.961  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00  24d+15:28:48.948  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00  24d+15:28:48.920  READ NATIVE MAX ADDRESS EXT

Error 6 occurred at disk power-on lifetime: 29892 hours (1245 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 80 ff ff ff 4f 00  24d+15:28:43.269  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00  24d+15:28:43.242  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00  24d+15:28:43.240  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00  24d+15:28:43.227  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00  24d+15:28:43.200  READ NATIVE MAX ADDRESS EXT

Error 5 occurred at disk power-on lifetime: 29892 hours (1245 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 80 ff ff ff 4f 00  24d+15:28:40.452  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00  24d+15:28:40.425  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00  24d+15:28:40.424  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00  24d+15:28:40.410  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00  24d+15:28:40.383  READ NATIVE MAX ADDRESS EXT

Error 4 occurred at disk power-on lifetime: 29892 hours (1245 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 a8 ff ff ff 4f 00  24d+15:28:34.700  READ FPDMA QUEUED
  60 00 80 ff ff ff 4f 00  24d+15:28:34.698  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00  24d+15:28:34.671  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00  24d+15:28:34.670  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00  24d+15:28:34.656  SET FEATURES [Set transfer mode]

Error 3 occurred at disk power-on lifetime: 29892 hours (1245 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 80 ff ff ff 4f 00  24d+15:28:31.899  READ FPDMA QUEUED
  60 00 a8 ff ff ff 4f 00  24d+15:28:31.898  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00  24d+15:28:31.871  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00  24d+15:28:31.869  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00  24d+15:28:31.856  SET FEATURES [Set transfer mode]

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

### Post by rubylaser on 2012-09-06
Your disk /dev/sdd has failed, so you're not going to be able to assemble the array with that disk. Also, /dev/sde doesn't look very heathly, it has a bunch of offline uncorrectable errors (68).  I would fail and remove /dev/sdd from the array.

```
mdadm --manage /dev/md0 --fail /dev/sdd1
```

Then, remove it from the array
```
mdadm --manage /dev/md0 --remove /dev/sdd1
```

Next, you'll need to stop the array
```
mdadm --stop /dev/md0
```

Update your /etc/mdadm/mdadm.conf file to reflect the correct number of disks.  You have 4 in your array, but your config only shows 3.

Finally, try to assemble your array degraded with the 3 remaining disks.
```
mdadm --assemble --force /dev/md0 /dev/sd[bce]1
```

Let me know how that goes.  You'll want to replace that failed disk with a new one, and you'll want to setup email alerts so that you are alerted when a disk fails a SMART test.

---

### Post by SeijiSensei on 2012-09-07
Just a recommendation.  If you get the array restarted using rubylaser's excellent instructions, you absolutely need to back up anything critical immediately.  Because of the way RAID5 works, if you lose that second wobbly drive, you won't be able to retrieve your data at all.  I rarely use RAID5 any more having been down the road of having only two drives left and no backups.  RAID1 is less efficient, but it has the nice feature that if one drive fails you can force Linux to mount the other one using the appropriate filesystem descriptor like ext4.  Backups are, of course, always the right thing to do, but being human I have been known to cut corners.

I will use RAID5 on machines with a dedicated hardware RAID controller and enterprise-class drives.  Consumer drives are more fragile, and something like a power surge can kill more than one of them at the same time.  When that happens you're stuck.  (That's a reason for investing in a good uninterruptible power supply.)

---

### Post by Rustafur on 2012-09-07
Thank you RubyLaser!  I'm so relieved to know that the array may be salvageable.  Thank you for the clear, and easy to follow instructions!  I'll try these out as soon as I have the time in the next day or so.

<backstory>
I have been aware of the "wobbly drive" (as it shall be referred to) for a couple weeks, and had already started purchasing replacement/upgrade HDD's to build a new array.  Two of the drives (2TB) arrived at my house a mere two days before this other drive went kaput.  So I do already have a replacement drive to try this out with. 

We had some bad storms roll through the morning this happened, and some other hardware around the house was acting a little funky, so I'm suspecting a power surge knocked out this HDD.  And I will definitely be immediately backing up everything to the spare 2TB HDD, if I'm able to resurrect this array. </end backstory>

---

### Post by Rustafur on 2012-09-07
> **SeijiSensei said:**
> Just a recommendation.  If you get the array restarted using rubylaser's excellent instructions, you absolutely need to back up anything critical immediately.  Because of the way RAID5 works, if you lose that second wobbly drive, you won't be able to retrieve your data at all.  I rarely use RAID5 any more having been down the road of having only two drives left and no backups.  RAID1 is less efficient, but it has the nice feature that if one drive fails you can force Linux to mount the other one using the appropriate filesystem descriptor like ext4.  Backups are, of course, always the right thing to do, but being human I have been known to cut corners.

I will use RAID5 on machines with a dedicated hardware RAID controller and enterprise-class drives.  Consumer drives are more fragile, and something like a power surge can kill more than one of them at the same time.  When that happens you're stuck.  (That's a reason for investing in a good uninterruptible power supply.)


I wouldn't mind going with a RAID1 setup at all, basically the reason I've been using a RAID5 setup is that I need the capacity/expand-ability.  This server is where I store all of my family's Movies/TV/Music/Pictures/.iso's/etc...  and in its tapped out at its current 1.8TB capacity.  I think currently, I would be stuck at about 3TB for a RAID1 setup, which I don't really see being "future proofed" enough for my needs.  I do, however, see a new UPS in my future now :)  But if you have any suggestions on how to get onto a more stable RAID platform, using consumer-level hardware, that can give me over 4TB of capacity, I would be open to any and all suggestions!

---

### Post by rubylaser on 2012-09-07
> **Rustafur said:**
> I wouldn't mind going with a RAID1 setup at all, basically the reason I've been using a RAID5 setup is that I need the capacity/expand-ability.  This server is where I store all of my family's Movies/TV/Music/Pictures/.iso's/etc...  and in its tapped out at its current 1.8TB capacity.  I think currently, I would be stuck at about 3TB for a RAID1 setup, which I don't really see being "future proofed" enough for my needs.  I do, however, see a new UPS in my future now :)  But if you have any suggestions on how to get onto a more stable RAID platform, using consumer-level hardware, that can give me over 4TB of capacity, I would be open to any and all suggestions!

Just go with RAID6 + a UPS then.  It's still expandable, and you will be able to survive the loss of 2 disks before losing your whole array.  This is much safer when dealing with massive drives.  But, as SeijiSensei mentioned, please make a backup of your critical data (home movies, family pictures, important documents), because even with RAID6, you could still lose your array, suffer data corruption, or something as simple as rm -rf the wrong directory.

---

### Post by Rustafur on 2012-09-07
I tried to run some of the commands RubyLaser sent.  First I tried setting sdd1 to fail, but mdadm returned "no such device" This same error returned when I tried to run the --remove command.  I believe this is is because my array's current state is Not Running.  Is that correct?  If so, can I just proceed on to modifying the mdadm.conf file, and then forcing the raid re-assembly with the 3 drives?


Another question.  I'm not that well versed in RAID5, so I'm having trouble understanding why starting the RAID array back up with the 3 remaining disks wouldn't result in data loss.  Is resetting the number of disks to 4 in the mdadm.conf file preventing this?  Thanks again for all the help, and knowledge sharing!

---

### Post by rubylaser on 2012-09-08
> **Rustafur said:**
> I tried to run some of the commands RubyLaser sent.  First I tried setting sdd1 to fail, but mdadm returned "no such device" This same error returned when I tried to run the --remove command.  I believe this is is because my array's current state is Not Running.  Is that correct?  If so, can I just proceed on to modifying the mdadm.conf file, and then forcing the raid re-assembly with the 3 drives?


Another question.  I'm not that well versed in RAID5, so I'm having trouble understanding why starting the RAID array back up with the 3 remaining disks wouldn't result in data loss.  Is resetting the number of disks to 4 in the mdadm.conf file preventing this?  Thanks again for all the help, and knowledge sharing!

If your array isn't running, I'd just turn the machine off, and remove the failed disk.  It's failed, so there's really no reason to leave it in the machine.  Then you can modify the mdadm.conf after you start it back up.  Finally, you are running a RAID5, so the array can survive with one missing disk, you'll just be running degraded with no protection from any other disks failing.

---

### Post by Rustafur on 2012-09-08
Shutdown the server, removed the sdd from the chassis, booted the server.  Edited mdadm.conf to show the correct number of disks (4), ran the mdadm --assemble --force command, and... no dice.

```
root@server:/home/administrator# mdadm --assemble --force /dev/md0 /dev/sd[bce]1
mdadm: metadata format 00.90 unknown, ignored.
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.
```

---

### Post by rubylaser on 2012-09-08
Since you removed /dev/sdd, /dev/sde would have probably become /dev/sdd.  What's the output of 

```
fdisk -l
```

and 
```
mdadm -E /dev/sd[bcd]1
```

If the the disk has moved, you'll need to assemble like this.
```
mdadm --assemble --force /dev/md0 /dev/sd[bcd]1
```

And one other stupid question, but you did check to make sure you pulled the correct disk? :)

---

### Post by darkod on 2012-09-08
Another short question. You said you edited mdadm.conf to show the correct number of disks (4), but shouldn't that be 3 right now? You count only the disks part of the array, not all disks in the system.
If there were 4 disks earlier, how can you still have 4 after removing one?

EDIT PS. Ignore this, the device count should still be 4, you are starting it as degraded array. Didn't think it trough. :)

---

### Post by Rustafur on 2012-09-08
You are correct RubyLaser, sde changed to sdd.  I feel a bit silly for not having caught that...

**fdiks -l**
```
root@server:/home/administrator# mdadm --assemble --force /dev/md0 /dev/sd[bce]1mdadm: metadata format 00.90 unknown, ignored.
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.
root@server:/home/administrator# gedit /etc/mdadm/mdadm.cof
root@server:/home/administrator# gedit /etc/mdadm/mdadm.conf
root@server:/home/administrator# mdadm --assemble --force /dev/md0 /dev/sd[bce]1mdadm: metadata format 00.90 unknown, ignored.
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.
root@server:/home/administrator# gedit /etc/mdadm/mdadm.confroot@server:/home/administrator# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00074c7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18663   149903360   83  Linux
/dev/sda2           18663       19458     6384641    5  Extended
/dev/sda5           18663       19458     6384640   82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000e28

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77825   625129281   fd  Linux raid autodetect

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe136be5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       77825   625129281   fd  Linux raid autodetect

Disk /dev/sdd: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00066404

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       77825   625129281   fd  Linux raid autodetect

```

**mdadm -E /dev/sd[bcd]1**
```
root@server:/home/administrator# mdadm -E /dev/sd[bcd]1
mdadm: metadata format 00.90 unknown, ignored.
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 286f028d:5d5ee152:01f9e43d:ac30fbff
  Creation Time : Wed Jun 30 21:40:10 2010
     Raid Level : raid5
  Used Dev Size : 625129216 (596.17 GiB 640.13 GB)
     Array Size : 1875387648 (1788.51 GiB 1920.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed Sep  5 16:41:12 2012
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 9edda200 - correct
         Events : 67498

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       0        0        1      faulty removed
   2     2       0        0        2      faulty removed
   3     3       8       33        3      active sync   /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 286f028d:5d5ee152:01f9e43d:ac30fbff
  Creation Time : Wed Jun 30 21:40:10 2010
     Raid Level : raid5
  Used Dev Size : 625129216 (596.17 GiB 640.13 GB)
     Array Size : 1875387648 (1788.51 GiB 1920.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed Sep  5 16:41:12 2012
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 9edda216 - correct
         Events : 67498

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       33        3      active sync   /dev/sdc1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       0        0        1      faulty removed
   2     2       0        0        2      faulty removed
   3     3       8       33        3      active sync   /dev/sdc1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 286f028d:5d5ee152:01f9e43d:ac30fbff
  Creation Time : Wed Jun 30 21:40:10 2010
     Raid Level : raid5
  Used Dev Size : 625129216 (596.17 GiB 640.13 GB)
     Array Size : 1875387648 (1788.51 GiB 1920.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed Sep  5 05:49:53 2012
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 9edd0958 - correct
         Events : 67478

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       65        2      active sync

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       0        0        1      faulty removed
   2     2       8       65        2      active sync
   3     3       8       33        3      active sync   /dev/sdc1

```

**mdadm --assemble --force /dev/md0**
```
root@server:/home/administrator# mdadm --assemble --force /dev/md0 /dev/sd[bcd]1mdadm: metadata format 00.90 unknown, ignored.
mdadm: forcing event count in /dev/sdd1(2) from 67478 upto 67498
mdadm: clearing FAULTY flag for device 2 in /dev/md0 for /dev/sdd1
mdadm: /dev/md0 has been started with 3 drives (out of 4).

```

Success!!!  The array is back online, I ran mount -a and the array successfully mounted correctly, and it looks like everything is there.

---

### Post by Rustafur on 2012-09-08
RubyLaser, I can't thank you enough for all the hand-holding you did with me on bringing my array back online.  You're truly a great example of the help and support available on these forums, and what makes this community so great.  Also, thank you to SeijiSensei for your input and suggestions :) 

I've started transferring everything over to a 2TB drive for temporary storage until I can get a new RAID array built up.  I'll be looking into RAID6, and possibly a hardware controller for sure.  Any suggestions on the hardware controller? :)

---

### Post by rubylaser on 2012-09-08
> **Rustafur said:**
> RubyLaser, I can't thank you enough for all the hand-holding you did with me on bringing my array back online.  You're truly a great example of the help and support available on these forums, and what makes this community so great.  Also, thank you to SeijiSensei for your input and suggestions :) 

I've started transferring everything over to a 2TB drive for temporary storage until I can get a new RAID array built up.  I'll be looking into RAID6, and possibly a hardware controller for sure.  Any suggestions on the hardware controller? :)

Great! I'm glad you got your array back online and I'm happy to help. 

Personally, I wouldn't use a hardware controller for home.  mdadm is very flexible and allowed you to survive 1 failed disk and 1 failing disk.  I also like not being locked into a particular hardware RAID card.  The only caveat with mdadm is that you do have to investigate some time to understand it's inner workings if you want to cope with tough situations like this.

---

### Post by SeijiSensei on 2012-09-08
Next item on the list should be a UPS.  I have an earlier model of [this APC unit]("http://www.newegg.com/Product/Product.aspx?Item=N82E16842101381").  I like APCs because there's an open-source monitoring daemon for Linux, [apcupsd]("https://help.ubuntu.com/community/apcupsd"), that checks that the power is on, shuts down the systems gracefully if the battery is running low, logs all power events, and sends you an email if the power goes down.

I also like the fact that APC is based in Rhode Island.

---

### Post by rubylaser on 2012-09-08
> **SeijiSensei said:**
> Next item on the list should be a UPS.  I have an earlier model of [this APC unit]("http://www.newegg.com/Product/Product.aspx?Item=N82E16842101381").  I like APCs because there's an open-source monitoring daemon for Linux, [apcupsd]("https://help.ubuntu.com/community/apcupsd"), that checks that the power is on, shuts down the systems gracefully if the battery is running low, logs all power events, and sends you an email if the power goes down.

I also like the fact that APC is based in Rhode Island.

+1 great advice.

---

### Post by Rustafur on 2012-09-08
Great advice, and I'll be taking it!  Thanks :)

---

