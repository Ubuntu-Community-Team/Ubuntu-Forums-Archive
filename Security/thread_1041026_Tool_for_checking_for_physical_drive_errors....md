---
title: "Tool for checking for physical drive errors..."
date: 2009-01-16
forum: Security
---

### Post by ragtag on 2009-01-16
I was helping a friend install a machine, and it kept failing to install at different points. Attempted two versions of Ubuntu and XP. Ubuntu generally seemed to hang during formating. I suspect it's a faulty drive, as I was able to boot the machine from several live cd's and an USB thumb drive.

 I'm looking for a tool that I can run of a live CD that will let me analyze the hard drive in the machine for physical errors. The drive is new and has nothing on it, but I suspect it's borked. What's a good tool for doing this?

 Any other suggestions as to what I should try?


p.s. My friend built the machine himself, but needs help installing the OS....so it may be a badly built machine. :)

---

### Post by hyper_ch on 2009-01-16
try a low-level format or run a "dd" from a live session over it:

```

sudo dd if=/dev/zero of=/dev/sdX

```

/dev/sdX should be the harddisk he wants to use and that command will overwrite everything on there.

---

### Post by ragtag on 2009-01-16
That sounds like a good idea. It is a 1TB drive, so will probably take quite a few hours.

Will it output errors if there are blocks it can't write to or i/o errors on the drive?

---

### Post by hyper_ch on 2009-01-16
yes, it should... and it will take some time...

---

### Post by caljohnsmith on 2009-01-16
I would suggest running a SMART test on the HDD, because then the HDD does its own internal self-test to determine its health. You can do that from Ubuntu by doing:
```
sudo apt-get install smartmontools
```
First do the following to save the current health status parameters of your HDD to a file on your desktop:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_before_test.txt
```
Then run:
```
sudo smartctl -t long /dev/sda
```
That command will immediately terminate while the HDD begins its self-test, and it could take quite a while. You can monitor the progress with:
```
sudo smartctl -a /dev/sda | grep -A 1 -i "self-test execution status"
```
Once the above command says the test is done, then do:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_after_test.txt
sudo smartctl -H /dev/sda
```
And please post the contents of the two files on your desktop so I can see the results. :)

---

### Post by ragtag on 2009-01-16
Thanks for the advice. I'm headed to my friends place armed with several Ubuntu versions, Knoppix, INSERT Live CD, Puppy and Damn Small Linux under my arm. I'll try the smart tools and post the result here once done. :)

---

### Post by hyper_ch on 2009-01-16
according to a massive google test s.m.a.r.t. does only report in 65% of the cases that a drive mgith be failing.

---

### Post by cariboo on 2009-01-16
The best thing to do is to go to the hard drives manufacturers web site and download their diagnostic tools. If there is a problem with the drive, the diagnostic tools will give you an error code, that you can use to get an RMA to return the drive for warranty.

Jim

---

### Post by ragtag on 2009-01-16
Hi,

 The first test ended with:

   ```

Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 

```

And the output in the text file was:

```

smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HD103UJ
Serial Number:    S13PJ90Q941329
Firmware Version: 1AA01113
User Capacity:    1,000,204,886,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 3b
Local Time is:    Fri Jan 16 18:34:48 2009 UTC

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (11395) seconds.
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
recommended polling time: 	 ( 191) minutes.
Conveyance self-test routine
recommended polling time: 	 (  20) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   076   076   011    Pre-fail  Always       -       8110
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       92
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       17
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       92
 13 Read_Soft_Error_Rate    0x000e   100   100   000    Old_age   Always       -       0
183 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       30
184 Unknown_Attribute       0x0033   100   100   000    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   082   068   000    Old_age   Always       -       18 (Lifetime Min/Max 18/18)
194 Temperature_Celsius     0x0022   078   067   000    Old_age   Always       -       22 (Lifetime Min/Max 18/22)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       1483
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   100   099   000    Old_age   Always       -       1
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 1
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

Error 1 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 53 73 dc 0a 34 e8  Error: ABRT at LBA = 0x08340adc = 137628380

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ca 00 80 cf 0a 34 e8 08      00:15:08.960  WRITE DMA
  ec 00 00 00 00 00 a0 08      00:15:08.960  IDENTIFY DEVICE
  ef 03 42 00 00 00 a0 08      00:15:08.950  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08      00:15:08.950  IDENTIFY DEVICE
  00 00 01 01 00 00 a0 08      00:15:08.790  NOP [Abort queued commands]

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

 That's it.

 Doesn't seem like there is too much wrong...if I'm making any sense of that data. Since it took ages, I'm going to give an install a shot, before attempting to run the second part you suggested.

---

### Post by ragtag on 2009-01-16
The installed failed...again.

Finally pulled out the screwdriver and opened up the machine. One of the memory chips was hanging half out of its slot. :)

Inserted all properly, but then the machine would go into an infinite re-boot loop every few seconds (never finished loading bios).

My guess now is broken RAM, and maybe motherboard.

Gave up for now...and went home to get some sleep.

---

