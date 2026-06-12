---
title: "mdadm raid5 drive failure"
date: 2009-06-01
forum: Server Platforms
---

### Post by wheniwork on 2009-06-01
I had a heat problem over the weekend with my MDADM RAID5. One of the drives supposedly failed. 

I think the controller just shut the HD down and now MDADM thinks its failed. 

How do I know for sure? Should I just do mdadm --assemble --force /dev/md0

Here is what SMART Tools gave me on the "failed" drive when scanned. Is it truly a dead drive?

I will post whatever info would help in determining what I should do. Reassemble array, replace the drive, etc?

```
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.10 family
Device Model:     ST3500630AS
Serial Number:    6QG16BKS
Firmware Version: 3.AAK
User Capacity:    500,107,862,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Jun  1 12:46:25 2009 CDT
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
data collection: 		 ( 430) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 163) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   106   093   006    Pre-fail  Always       -       77490784
  3 Spin_Up_Time            0x0003   093   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       141
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       1
  7 Seek_Error_Rate         0x000f   072   054   030    Pre-fail  Always       -       69010122065
  9 Power_On_Hours          0x0032   085   085   000    Old_age   Always       -       13209
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       133
187 Unknown_Attribute       0x0032   094   094   000    Old_age   Always       -       6
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   064   038   045    Old_age   Always   In_the_past 707002404
194 Temperature_Celsius     0x0022   036   062   000    Old_age   Always       -       36 (Lifetime Min/Max 0/16)
195 Hardware_ECC_Recovered  0x001a   062   058   000    Old_age   Always       -       129785447
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       4
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 10 (device log contains only the most recent five errors)
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

Error 10 occurred at disk power-on lifetime: 13174 hours (548 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 97 28 8d 32 e1  Error: ICRC, ABRT 151 sectors at LBA = 0x01328d28 = 20090152

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 d8 e7 8c 32 e1 00      07:16:11.293  READ DMA
  c8 00 a8 3f 8c 32 e1 00      07:16:11.238  READ DMA
  c8 00 08 8f 8f 59 ee 00      07:16:11.160  READ DMA
  c8 00 80 bf e4 2c e1 00      07:16:11.695  READ DMA
  c8 00 08 b7 e4 2c e1 00      07:16:11.672  READ DMA

Error 9 occurred at disk power-on lifetime: 13174 hours (548 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 27 98 58 0c eb  Error: ICRC, ABRT 39 sectors at LBA = 0x0b0c5898 = 185358488

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 58 67 58 0c eb 00      07:16:00.647  READ DMA
  c8 00 28 3f 58 0c eb 00      07:16:00.607  READ DMA
  c8 00 80 bf 4a 0c eb 00      07:16:00.587  READ DMA
  c8 00 48 3f 4e 0c eb 00      07:16:00.581  READ DMA
  c8 00 80 3f 36 0c eb 00      07:16:00.560  READ DMA

Error 8 occurred at disk power-on lifetime: 13174 hours (548 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 3f 80 4c 0c eb  Error: ICRC, ABRT 63 sectors at LBA = 0x0b0c4c80 = 185355392

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 80 3f 4c 0c eb 00      07:15:59.596  READ DMA
  c8 00 80 bf 4b 0c eb 00      07:15:59.582  READ DMA
  c8 00 80 3f 4b 0c eb 00      07:15:59.572  READ DMA
  c8 00 80 bf b0 0d eb 00      07:15:59.532  READ DMA
  c8 00 80 3f e3 08 eb 00      07:15:59.456  READ DMA

Error 7 occurred at disk power-on lifetime: 13174 hours (548 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 9f 20 5d 0c eb  Error: ICRC, ABRT 159 sectors at LBA = 0x0b0c5d20 = 185359648

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 00 bf 5c 0c eb 00      07:15:57.114  READ DMA
  c8 00 80 3f 5c 0c eb 00      07:15:57.052  READ DMA
  c8 00 80 3f 3b 0e eb 00      07:15:57.032  READ DMA
  c8 00 48 f7 3a 0e eb 00      07:15:57.000  READ DMA
  c8 00 20 d7 3a 0e eb 00      07:15:56.996  READ DMA

Error 6 occurred at disk power-on lifetime: 631 hours (26 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ce 92 64 e0  Error: UNC at LBA = 0x006492ce = 6591182

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 3f 91 64 e0 00      04:26:20.329  READ DMA EXT
  27 00 00 00 00 00 e0 00      04:26:20.314  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 02      04:26:20.255  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 02      04:26:20.239  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      04:26:18.186  READ NATIVE MAX ADDRESS EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     13208         -
# 2  Short offline       Aborted by host               60%     13206         -
# 3  Extended offline    Completed without error       00%       920         -
# 4  Short offline       Completed without error       00%       918         -
# 5  Short offline       Interrupted (host reset)      40%       914         -

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

### Post by grantemsley on 2009-06-01
WARNING: I am not an expert with software raid (yet).  I know a fair bit but not everything!

According to the SMART info there, your hard drive has had to reallocate one sector (because the old one failed), and has had CRC errors.

IIRC, CRC errors are usually caused by bad cables, so I'd check that.

If you are pretty sure it was just heat problems (and have corrected the heat problem), you can probably keep using that drive.  If it contains really important stuff and you don't have backups, I'd backup and replace the drive.

You can use smartctl -t long /dev/whatever to run a full test of the drive, then check the smartctl output again.  If the CRC error or reallocated sectors increases after the test - throw the drive out and replace it, because the drive is probably starting to fail.

---

### Post by wheniwork on 2009-06-01
Ok. I ordered a new drive just to be safe. The data is pretty important.

What do you recommend for a good mdadm tutorial on replacing a failed drive and rebuilding the array?

---

### Post by grantemsley on 2009-06-02
I've found [http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html) pretty useful, but don't use the raid* commands, they are outdated, use the mdadm commands.

The basic procedure is:
mdadm /dev/md0 -r /dev/sd?? (remove the failed drive)
Pull the drive, add in a replacement.  Partition it if your array is on partitions, then:
mdadm /dev/md0 -a /dev/sd?? (add the new drive)

Then "watch cat /proc/mdstat" to watch it rebuild.  There are some parameters you can tweak if you want it to rebuild faster (and in the process hurt all other disk IO from the array

```

echo 200000 > /proc/sys/dev/raid/speed_limit_max
echo 200000 > /proc/sys/dev/raid/speed_limit_min

```
That will set the max and min rebuild speed to 200MB/s, which should be as fast as possible.  The defaults are fairly low IIRC.

---

### Post by fjgaude on 2009-06-02
Here's more links:

[http://linux-raid.osdl.org/index.php/Main_Page](http://linux-raid.osdl.org/index.php/Main_Page)
[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)

Have fun!

---

### Post by wheniwork on 2009-06-02
Here is the situation now.

We are running Ubuntu Server 8.04 and using Linux Raid (mdadm). We had a drive fail (/dev/sdi1). 

The array then automatically removed the drive and degraded the array. 

This morning I replaced the physical drive and rebooted the machine. 

I partitioned the new drive (now named /dev/sdk1). 

Now the array device /dev/md0 is not active. I think this is because the device names got changed so the array is confused now.

Where I am at now is the re assembly of the array. I want to make sure I do it right so nothing is lost. Basically we have a total of 10 drives, 9 are fine, 1 is new. However, the names of the devices changed when I replaced the failed drive so now the array device (/dev/md0) is not active and probably confused (which is why it's not working/mounting). 

Any thoughts would be helpful?

---

