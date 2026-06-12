---
title: "Hard drive errors? or not?"
date: 2014-11-20
forum: Server Platforms
---

### Post by CGW on 2014-11-20
I just setup a new Ubuntu 14.04.1 server to replace a faulty mobo of my previous server box. However, right out of the gate I have an odd warning. After logging into webmin I'm greeted with the dreaded warning my boot drive has numerous hard drive issues. I ran smartmontools (long test) and sudo touch /forcefsck and both say everything is fine. 

Is it or is it not? I've never been adept at reading the smartmontools output. But it clearly says PASSED.

I'm at a loss as to any additional info would helpful. 

Thanks in advance.

Screenshot:
[http://cworkman.us/1F8Ks0r](http://cworkman.us/1F8Ks0r)

[IMG]http://dl.dropboxusercontent.com/s/xymadcrd5wselv6/Screenshot%202014-11-20%2021.08.49.png?dl=0[/IMG]

```
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-39-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar SE Serial ATA
Device Model:     WDC WD2000JD-98HBB0
Serial Number:    WD-WCAL81257480
Firmware Version: 08.02D08
User Capacity:    200,049,647,616 bytes [200 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA/ATAPI-6 (minor revision not indicated)
Local Time is:    Thu Nov 20 21:35:50 2014 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x85)	Offline data collection activity
					was aborted by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		( 5785) seconds.
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
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  75) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   200   192   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   120   120   021    Pre-fail  Always       -       6508
  4 Start_Stop_Count        0x0032   092   092   040    Old_age   Always       -       8813
  5 Reallocated_Sector_Ct   0x0033   199   199   140    Pre-fail  Always       -       4
  7 Seek_Error_Rate         0x000b   200   200   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   035   035   000    Old_age   Always       -       47895
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0013   100   100   051    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   096   096   000    Old_age   Always       -       4843
194 Temperature_Celsius     0x0022   109   095   000    Old_age   Always       -       41
196 Reallocated_Event_Count 0x0032   199   199   000    Old_age   Always       -       1
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0012   200   200   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age   Always       -       18
200 Multi_Zone_Error_Rate   0x0009   200   200   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 692 (device log contains only the most recent five errors)
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

Error 692 occurred at disk power-on lifetime: 2516 hours (104 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 80 d3 4a b4 e0  Error: UNC 128 sectors at LBA = 0x00b44ad3 = 11815635

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 80 70 4a b4 11 00      00:16:56.450  READ DMA EXT
  35 00 80 88 2c c3 15 00      00:16:56.450  WRITE DMA EXT
  25 00 80 40 93 b8 12 00      00:16:56.450  READ DMA EXT
  35 00 80 08 2c c3 15 00      00:16:56.450  WRITE DMA EXT
  25 00 80 c0 92 b8 12 00      00:16:56.450  READ DMA EXT

Error 691 occurred at disk power-on lifetime: 2516 hours (104 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 80 d3 4a b4 e0  Error: UNC 128 sectors at LBA = 0x00b44ad3 = 11815635

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 80 70 4a b4 11 00      00:16:21.400  READ DMA EXT
  35 00 80 40 93 b8 12 00      00:16:21.400  WRITE DMA EXT
  25 00 80 88 2c c3 15 00      00:16:21.400  READ DMA EXT
  35 00 80 c0 92 b8 12 00      00:16:21.400  WRITE DMA EXT
  25 00 80 08 2c c3 15 00      00:16:21.400  READ DMA EXT

Error 690 occurred at disk power-on lifetime: 2516 hours (104 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 80 d3 4a b4 e0  Error: UNC 128 sectors at LBA = 0x00b44ad3 = 11815635

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 80 70 4a b4 11 00      00:15:48.900  READ DMA EXT
  35 00 80 88 2c c3 15 00      00:15:48.900  WRITE DMA EXT
  25 00 80 40 93 b8 12 00      00:15:48.900  READ DMA EXT
  35 00 80 08 2c c3 15 00      00:15:48.900  WRITE DMA EXT
  25 00 80 c0 92 b8 12 00      00:15:48.900  READ DMA EXT

Error 689 occurred at disk power-on lifetime: 2516 hours (104 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 80 d3 4a b4 e0  Error: UNC 128 sectors at LBA = 0x00b44ad3 = 11815635

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 80 70 4a b4 11 00      00:15:16.250  READ DMA EXT
  35 00 80 40 93 b8 12 00      00:15:16.250  WRITE DMA EXT
  25 00 80 88 2c c3 15 00      00:15:16.250  READ DMA EXT
  35 00 80 c0 92 b8 12 00      00:15:16.250  WRITE DMA EXT
  25 00 80 08 2c c3 15 00      00:15:16.250  READ DMA EXT

Error 688 occurred at disk power-on lifetime: 2516 hours (104 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 80 d3 4a b4 e0  Error: UNC 128 sectors at LBA = 0x00b44ad3 = 11815635

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 80 70 4a b4 11 00      00:14:40.350  READ DMA EXT
  35 00 80 88 2c c3 15 00      00:14:40.350  WRITE DMA EXT
  25 00 80 40 93 b8 12 00      00:14:40.350  READ DMA EXT
  35 00 80 08 2c c3 15 00      00:14:40.350  WRITE DMA EXT
  25 00 80 c0 92 b8 12 00      00:14:40.350  READ DMA EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     47888         -
# 2  Short offline       Completed without error       00%     47887         -
# 3  Conveyance offline  Completed without error       00%     30051         -
# 4  Short offline       Completed without error       00%     10840         -

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

### Post by xubuntu84 on 2014-11-20
Hello,

I too have been unfamiliar with smartctl output.  However, I've been doing a bit of research lately for similar problems.

[This page]("http://ubuntuforums.org/showthread.php?t=2192335") is pretty helpful with understanding how to read the table.

```

SMART Attributes Data Structure revision number: 16
Vendor  Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG    VALUE   WORST   THRESH  TYPE        UPDATED WHEN_FAILED     RAW_VALUE
1   Raw_Read_Error_Rate     0x000b  200     192     051     Pre-fail    Always -                0
3   Spin_Up_Time            0x0007  120     120     021     Pre-fail    Always -                6508
4   Start_Stop_Count        0x0032  092     092     040     Old_age     Always -                8813
5   Reallocated_Sector_Ct   0x0033  199     199     140     Pre-fail    Always -                4
7   Seek_Error_Rate         0x000b  200     200     051     Pre-fail    Always -                0
9   Power_On_Hours          0x0032  035     035     000     Old_age     Always -                47895
10  Spin_Retry_Count        0x0013  100     100     051     Pre-fail    Always -                0
11  Calibration_Retry_Count 0x0013  100     100     051     Pre-fail    Always -                0
12  Power_Cycle_Count       0x0032  096     096     000     Old_age     Always -                4843
194 Temperature_Celsius     0x0022  109     095     000     Old_age     Always -                41
196 Reallocated_Event_Count 0x0032  199     199     000     Old_age     Always -                1
197 Current_Pending_Sector  0x0012  200     200     000     Old_age     Always -                0
198 Offline_Uncorrectable   0x0012  200     200     000     Old_age     Always -                0
199 UDMA_CRC_Error_Count    0x000a  200     253     000     Old_age     Always -                18
200 Multi_Zone_Error_Rate   0x0009  200     200     051     Pre-fail    Offline -               0

```

Based on the errors from the long test, and your UDMA_CRC_Error_Count, I would check your SATA hardware.  Specifically:

[LIST]
[*]bad cable 
[*]bad connector 
[*]cable is too long 
[*]power supply is insufficient 
[/LIST]

This info was obtained from [here]("http://jmtd.net/log/is_my_drive_dying/") and [here]("http://superuser.com/questions/641219/possibly-a-dying-hard-drive-but-reads-writes-work-unsure-about-log-entries").

Like I said though, I'm not all that adept at troubleshooting failing drives just yet.

Good luck!
Ben

---

### Post by CGW on 2014-11-21
Thanks for the reply. 

That would make sense. The cable for that drive was one I pulled from another unit. I'll replace the cable and see what happens.

Thanks for the info.

---

### Post by tgalati4 on 2014-11-22
At almost 50k hours, it's possible that your drive has some intermittent faults--either electrical or mechanical.  Vibration of the drive could cause a loose connection which will cause dropouts.  Check the vibration level by putting your hand on the metal cover side of the drive.  Check the screws and carriage to make sure it is not loose.  It's also possible that solder cold junctions or aging drive electronics can cause similar issues.  Of course, a weak power supply during boot-up will cause errors that go away once the PSU is warmed up and the disk is spinning.

---

### Post by CGW on 2014-11-22
Wellll, I've ordered a new batch of SATA sables and am going to relocate the boot drive inside the case when they arrive. My question right now: Is it dangerous to allow the drive/system to run as-is until then?

Thanks again!

---

### Post by CGW on 2014-11-22
lol, I guess I could just stop being lazy and replace the drive. :(

---

### Post by tgalati4 on 2014-11-23
I had an old IDE drive with about 50K hours on it and over 600 days of uptime on a Dapper Drake server.  I was getting intermittent IDE bus errors and IO Waits.  The power connector had vibrated loose from the back of the drive!  I cleaned out the machine, reseated everything, and put some tie straps to secure the power plug.  So it's possible to get lots of drive errors and yet have passing SMART status.

In regards to using your drive in its current condition, it's OK until you lose data, then it is not OK.

You could put the drive in an external USB enclosure and use it for static backups.  Drives with 50K hours tend to have sticky bearings, so even using them for static storage is risky, because they may not spin up after 3 months or a year of storage.

---

### Post by CGW on 2014-11-24
I'm going to move the drive to a different SATA point to verify if the port itself has issues. If not, I'll just bit the bullet and replace the drive as I've already replaced the cable itself. 

Thanks again for your assistance.

---

