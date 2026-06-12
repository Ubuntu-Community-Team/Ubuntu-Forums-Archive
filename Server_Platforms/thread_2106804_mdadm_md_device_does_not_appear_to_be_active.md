---
title: "mdadm md device does not appear to be active ?"
date: 2013-01-20
forum: Server Platforms
---

### Post by Boker939 on 2013-01-20
Hi 
 
No longer able to access my raid, not sure what caused this, but im not able to start it either, help!
 
mdadm -E /dev/md0 
mdadm: no md superblock detected on /dev/md0
 
mdadm -D /dev/md0
mdadm: md device /dev/md0 does not appear to be active
 
cat /proc/mdstat shows 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
 
md0: inactive sdb1[2](S)  sdc1[1](S)  sde1[0](S)
5860535808 blocks
 
unused devices:<none>
 
I thought a disk may have failed since I have 4 disks in this array and only appears to show 3 in the above, I tried to --run the raid and go the below:
 
mdadm: failed to run array /dev/md0: Input/output error.
 
 
Is it possible to reassemable this raid?
 
thanks

---

### Post by rubylaser on 2013-01-20
Can you run smartmontools on all of the disks in your array and post the results back?
```
apt-get install smartmontools
smartctl -a /dev/sdb
smartctl -a /dev/sdc
smartctl -a /dev/sdd
smartctl -a /dev/sde
```

Also, can you paste the results of this too?
```
cat /etc/mdadm/mdadm.conf
```

and
```
mdadm -E /dev/sd[bcde]
```

---

### Post by Boker939 on 2013-01-21
```


matt@OptimusPrime:~$ sudo mdadm -E /dev/sd[bcde]
mdadm: No md superblock detected on /dev/sdb.
mdadm: No md superblock detected on /dev/sdc.
mdadm: No md superblock detected on /dev/sdd.
mdadm: No md superblock detected on /dev/sde.
matt@OptimusPrime:~$ cat /etc/mdadm/mdadm.conf
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=dc256ec9:45cdecc4:fbf2ea5a:12bfd232

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

# This file was auto-generated on Sun, 20 Nov 2011 18:58:19 +1100
# by mkconf $Id$







matt@OptimusPrime:~$ sudo smartctl -a /dev/sde
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WCAZA4779754
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Jan 21 17:04:29 2013 EST
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
data collection: 		 (36060) seconds.
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
SCT capabilities: 	       (0x3035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   192   192   051    Pre-fail  Always       -       5047
  3 Spin_Up_Time            0x0027   253   171   021    Pre-fail  Always       -       983
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       268
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       13
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   081   081   000    Old_age   Always       -       14288
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       156
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       54
193 Load_Cycle_Count        0x0032   186   186   000    Old_age   Always       -       44144
194 Temperature_Celsius     0x0022   114   111   000    Old_age   Always       -       36
196 Reallocated_Event_Count 0x0032   188   188   000    Old_age   Always       -       12
197 Current_Pending_Sector  0x0032   196   196   000    Old_age   Always       -       1336
198 Offline_Uncorrectable   0x0030   200   199   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   001   000    Old_age   Offline      -       74

SMART Error Log Version: 1
ATA Error Count: 16 (device log contains only the most recent five errors)
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

Error 16 occurred at disk power-on lifetime: 11324 hours (471 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 45 00 00 00 a0  Device Fault; Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 03 45 00 00 00 a0 08  11d+21:55:49.598  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08  11d+21:55:49.577  IDENTIFY DEVICE
  ec 00 00 00 00 00 a0 08  11d+21:55:44.111  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08  11d+21:55:44.083  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08  11d+21:55:44.062  IDENTIFY DEVICE

Error 15 occurred at disk power-on lifetime: 11324 hours (471 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 45 00 00 00 a0  Device Fault; Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 03 45 00 00 00 a0 08  11d+21:55:44.083  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08  11d+21:55:44.062  IDENTIFY DEVICE
  ec 00 00 00 00 00 a0 08  11d+21:55:38.605  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08  11d+21:55:38.579  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08  11d+21:55:38.558  IDENTIFY DEVICE

Error 14 occurred at disk power-on lifetime: 11324 hours (471 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 45 00 00 00 a0  Device Fault; Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 03 45 00 00 00 a0 08  11d+21:55:38.579  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08  11d+21:55:38.558  IDENTIFY DEVICE
  ec 00 00 00 00 00 a0 00  11d+21:55:38.029  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00  11d+21:55:38.009  SET FEATURES [Set transfer mode]

Error 13 occurred at disk power-on lifetime: 11324 hours (471 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 46 00 00 00 a0  Device Fault; Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 03 46 00 00 00 a0 00  11d+21:55:38.009  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00  11d+21:55:37.989  IDENTIFY DEVICE
  ec 00 00 00 00 00 a0 00  11d+21:55:37.969  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00  11d+21:55:37.949  SET FEATURES [Set transfer mode]

Error 12 occurred at disk power-on lifetime: 11324 hours (471 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 46 00 00 00 a0  Device Fault; Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 03 46 00 00 00 a0 00  11d+21:55:37.949  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00  11d+21:55:37.929  IDENTIFY DEVICE
  ec 00 00 00 00 00 a0 00  11d+21:55:37.899  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00  11d+21:55:37.879  SET FEATURES [Set transfer mode]

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

matt@OptimusPrime:~$ 


matt@OptimusPrime:~$ sudo smartctl -a /dev/sdb
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EARX-00PASB0
Serial Number:    WD-WCAZAC261539
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Jan 21 17:04:55 2013 EST
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
data collection: 		 (38160) seconds.
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
SCT capabilities: 	       (0x3035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   169   164   021    Pre-fail  Always       -       6533
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       89
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   086   086   000    Old_age   Always       -       10435
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       87
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       45
193 Load_Cycle_Count        0x0032   189   189   000    Old_age   Always       -       33719
194 Temperature_Celsius     0x0022   113   107   000    Old_age   Always       -       37
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

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

matt@OptimusPrime:~$ 
matt@OptimusPrime:~$ sudo smartctl -a /dev/sdc
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WMAZA0523485
Firmware Version: 50.0AB50
User Capacity:    2,000,398,934,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Jan 21 17:05:42 2013 EST
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
data collection: 		 (36000) seconds.
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
SCT capabilities: 	       (0x3035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       10
  3 Spin_Up_Time            0x0027   166   158   021    Pre-fail  Always       -       6691
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1004
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   076   076   000    Old_age   Always       -       17722
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       231
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       80
193 Load_Cycle_Count        0x0032   177   177   000    Old_age   Always       -       70514
194 Temperature_Celsius     0x0022   109   106   000    Old_age   Always       -       41
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

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

matt@OptimusPrime:~$ 


att@OptimusPrime:~$ sudo smartctl -a /dev/sdd
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     ST31000333AS
Serial Number:    9TE1038Y
Firmware Version: CC1H
User Capacity:    1,000,204,886,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Mon Jan 21 17:06:36 2013 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 625) seconds.
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
recommended polling time: 	 ( 213) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x103f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   117   099   006    Pre-fail  Always       -       144947860
  3 Spin_Up_Time            0x0003   100   094   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       753
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   076   060   030    Pre-fail  Always       -       42890255
  9 Power_On_Hours          0x0032   084   084   000    Old_age   Always       -       14699
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       3
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       590
184 Unknown_Attribute       0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   099   098   000    Old_age   Always       -       12885098623
189 High_Fly_Writes         0x003a   001   001   000    Old_age   Always       -       157
190 Airflow_Temperature_Cel 0x0022   058   042   045    Old_age   Always   In_the_past 42 (0 28 42 41)
194 Temperature_Celsius     0x0022   042   058   000    Old_age   Always       -       42 (0 17 0 0)
195 Hardware_ECC_Recovered  0x001a   027   023   000    Old_age   Always       -       144947860
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       254433862629190
241 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       2255223822
242 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       162014389

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

### Post by Boker939 on 2013-01-21
Im able to see the details now of MD0, but it appeared two disks have been removed... not sure if the below information will be helpful

```


matt@OptimusPrime:~$ sudo mdadm --detail /dev/md0
mdadm: md device /dev/md0 does not appear to be active.
matt@OptimusPrime:~$ sudo mdadm --run /dev/md0
mdadm: failed to run array /dev/md0: Input/output error
matt@OptimusPrime:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Thu Nov 24 18:01:12 2011
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Jan 21 16:40:08 2013
          State : active, degraded, Not Started
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : dc256ec9:45cdecc4:fbf2ea5a:12bfd232 (local to host OptimusPrime)
         Events : 0.90803

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       33        1      active sync   /dev/sdc1
       2       8       17        2      active sync   /dev/sdb1
       3       0        0        3      removed
matt@OptimusPrime:~$ 
matt@OptimusPrime:~$ sudo mdadm --examine /dev/sd[bcde]1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : dc256ec9:45cdecc4:fbf2ea5a:12bfd232 (local to host OptimusPrime)
  Creation Time : Thu Nov 24 18:01:12 2011
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
   Raid Devices : 4
  Total Devices : 2
Preferred Minor : 0

    Update Time : Mon Jan 21 16:40:08 2013
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : ee0ec535 - correct
         Events : 90803

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       17        2      active sync   /dev/sdb1

   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       0        0        3      faulty removed
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : dc256ec9:45cdecc4:fbf2ea5a:12bfd232 (local to host OptimusPrime)
  Creation Time : Thu Nov 24 18:01:12 2011
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
   Raid Devices : 4
  Total Devices : 2
Preferred Minor : 0

    Update Time : Mon Jan 21 16:40:08 2013
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : ee0ec543 - correct
         Events : 90803

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       0        0        3      faulty removed
mdadm: No md superblock detected on /dev/sdd1.
/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : dc256ec9:45cdecc4:fbf2ea5a:12bfd232 (local to host OptimusPrime)
  Creation Time : Thu Nov 24 18:01:12 2011
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Mon Jan 21 16:10:12 2013
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 1
       Checksum : ee102159 - correct
         Events : 90796

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       65        4      spare   /dev/sde1

   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       0        0        3      faulty removed
   4     4       8       65        4      spare   /dev/sde1
matt@OptimusPrime:~$

```

---

### Post by rubylaser on 2013-01-21
Looks like most of your disks are healthy (except sde).  /dev/sde has a bunch of pending sectors and reallocated sectors. I would be RMAing that if it's still under warranty. Unfortunately, you can't do that right now, because you only have 3 of your 4 disks with a mdadm superblock.

I hope you have a backup, because it's likely that forcing the array together and reassembling will push see over the edge. Luckily, your event counters are very close on the remaining disks, so this should be able to be assembled. This should get your array assembled (obviously with 1 missing disk). 

```
sudo -i
mdadm --stop /dev/md0
mdadm --assemble --force /dev/md0 /dev/sd[bce]1
```

---

### Post by Boker939 on 2013-01-21
I tried to run this but get the below message 

```

root@OptimusPrime:~# mdadm --stop /dev/md0
mdadm: stopped /dev/md0
root@OptimusPrime:~# mdadm --assemble --force /dev/md0 /dev/sd[bce]1
mdadm: /dev/md0 assembled from 2 drives and 1 spare - not enough to start the array.

```

Could this be because sde1 was accidentally removed from the array?

Is there a way it can be re-added? it wasnt --failed, only --remove from /dev/md0. I was attempting to remove the sdd and hit sde instead...

---

### Post by rubylaser on 2013-01-22
This sounds like a mess... You are not going to be able to --add that disk back because the array needs to be running to use the --add command.  Based on what I've seen and you've said,  it appears that you only have 2 of your 4 disks that are available as part of your array now.

At this point, you are probably going to need to re-create your array with the --assume-clean flag and the missing disk option so that your array won't cause a re-sync event.

---

