---
title: "Gazelle lag"
date: 2013-02-14
forum: System76 Support
---

### Post by tjw9767 on 2013-02-14
Hello all, I'm new to the forum but I've been using linux for a few years now. I have encountered some obscure lag with my Gazelle pro, when I'm running applications it will run for a few seconds then stop and repeat that cycle. I thought it was an issue with ubuntu so I did a fresh install and that didn't work. Now I'm dual booting with windows 7 and mint 14 and having the same problem on both partitions. Is this a hardware issue that can be fixed, or do I need a new laptop?

Thank you in advance
--Tyler

---

### Post by lolwtfhax on 2013-02-14
It may be a hardware issue if both linux and windows are doing this. Does it tend to happen when there is disk activity or all the time?

To test your hdd install smartmontools:
sudo apt-get install smartmontools

Run test with:
sudo smartctl -t short /dev/sda
 - this runs a short SMART test which takes 2 - 5 minutes to complete. You can view the status with:
sudo smartctl -a /dev/sda

To run an extended test which can take a couple hours to complete use:
sudo smartctl -t long /dev/sda


You can also run a memtest from most livecds to check ram, though an issue with memory would likely be causing programs to crash. The lag you're describing leads me to believe it's an issue with the HDD.

---

### Post by tjw9767 on 2013-02-14
I have the issues on both windows and linux. I tried doing a fresh install of ubuntu in the past, and more recently partitioning it to windows 7 and mint 14 and the problem is on both.

Just ran the test and I'm not 100% sure what I'm looking at here

```
=== START OF INFORMATION SECTION ===
Device Model:     Seagate ST95005620AS
Serial Number:    5YX1BDR8
LU WWN Device Id: 5 000c50 03d918bbf
Firmware Version: TD27
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Thu Feb 14 12:01:12 2013 EST
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
data collection: 		(  625) seconds.
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
recommended polling time: 	 ( 104) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x1001)	SCT Status supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   115   093   006    Pre-fail  Always       -       97458687
  3 Spin_Up_Time            0x0003   097   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       989
  5 Reallocated_Sector_Ct   0x0033   098   098   036    Pre-fail  Always       -       59
  7 Seek_Error_Rate         0x000f   073   060   030    Pre-fail  Always       -       4318175166
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1397
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       1011
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       282
188 Command_Timeout         0x0032   100   253   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   057   046   045    Old_age   Always       -       43 (Min/Max 25/43)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       78
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       1828
194 Temperature_Celsius     0x0022   043   054   000    Old_age   Always       -       43 (0 13 0 0 0)
195 Hardware_ECC_Recovered  0x001a   042   034   000    Old_age   Always       -       97458687
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 22 (device log contains only the most recent five errors)
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

Error 22 occurred at disk power-on lifetime: 624 hours (26 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 f0 ff ff ff 5f  Error: UNC 240 sectors at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff 0f 00   5d+11:16:11.207  READ DMA EXT
  25 00 f0 ff ff ff 0f 00   5d+11:15:54.172  READ DMA EXT
  25 00 08 ff ff ff 0f 00   5d+11:15:52.221  READ DMA EXT
  25 00 08 ff ff ff 0f 00   5d+11:15:48.194  READ DMA EXT
  25 00 f0 ff ff ff 0f 00   5d+11:15:30.885  READ DMA EXT

Error 21 occurred at disk power-on lifetime: 624 hours (26 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 f0 ff ff ff 5f  Error: UNC 240 sectors at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff 0f 00   4d+16:33:02.935  READ DMA EXT
  25 00 f0 ff ff ff 0f 00   4d+16:32:45.918  READ DMA EXT
  25 00 08 ff ff ff 0f 00   4d+16:32:43.972  READ DMA EXT
  25 00 08 ff ff ff 0f 00   4d+16:32:39.938  READ DMA EXT
  25 00 f0 ff ff ff 0f 00   4d+16:32:22.940  READ DMA EXT

Error 20 occurred at disk power-on lifetime: 624 hours (26 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 f0 ff ff ff 5f  Error: UNC 240 sectors at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff 0f 00  20d+17:52:47.041  READ DMA EXT
  25 00 f0 ff ff ff 0f 00  20d+17:52:30.410  READ DMA EXT
  25 00 08 ff ff ff 0f 00  20d+17:52:27.987  READ DMA EXT
  25 00 08 ff ff ff 0f 00  20d+17:52:23.928  READ DMA EXT
  25 00 f0 ff ff ff 0f 00  20d+17:52:06.621  READ DMA EXT

Error 19 occurred at disk power-on lifetime: 624 hours (26 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 f0 ff ff ff 5f  Error: UNC 240 sectors at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff 0f 00  19d+17:51:41.483  READ DMA EXT
  25 00 f0 ff ff ff 0f 00  19d+17:51:24.476  READ DMA EXT
  25 00 08 ff ff ff 0f 00  19d+17:51:22.529  READ DMA EXT
  25 00 08 ff ff ff 0f 00  19d+17:51:18.500  READ DMA EXT
  25 00 f0 ff ff ff 0f 00  19d+17:51:01.510  READ DMA EXT

Error 18 occurred at disk power-on lifetime: 624 hours (26 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 f0 ff ff ff 5f  Error: UNC 240 sectors at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff 0f 00   6d+02:58:01.592  READ DMA EXT
  25 00 f0 ff ff ff 0f 00   6d+02:57:45.654  READ DMA EXT
  25 00 08 ff ff ff 0f 00   6d+02:57:43.956  READ DMA EXT
  25 00 08 ff ff ff 0f 00   6d+02:57:39.032  READ DMA EXT
  25 00 f0 ff ff ff 0f 00   6d+02:57:23.009  READ DMA EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      1397         -

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

### Post by lolwtfhax on 2013-02-15
> # 1  Short offline       Completed without error       00%      1397         -

That means it passed a short test. However, These errors are something to be concerned about:
>   25 00 08 ff ff ff 0f 00   5d+11:16:11.207  READ DMA EXT
  25 00 f0 ff ff ff 0f 00   5d+11:15:54.172  READ DMA EXT
  25 00 08 ff ff ff 0f 00   5d+11:15:52.221  READ DMA EXT
  25 00 08 ff ff ff 0f 00   5d+11:15:48.194  READ DMA EXT
  25 00 f0 ff ff ff 0f 00   5d+11:15:30.885  READ DMA EXT

I'd recommend running the long test. Most likely the drive is failing.

---

