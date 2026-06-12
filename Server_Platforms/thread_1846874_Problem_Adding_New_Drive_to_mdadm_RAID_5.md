---
title: "Problem Adding New Drive to mdadm RAID 5"
date: 2011-09-19
forum: Server Platforms
---

### Post by littlegreiger on 2011-09-19
My current RAID 5 array consisted of 3x2TB WD Caviar Green hard drives and I wanted to add another drive to it so I purchased another 2TB WD Caviar Green and grew the array using ```
mdadm --add /dev/md0 /dev/sde
mdadm --grow /dev/md0 --raid-devices=4
```and left it to run overnight. Upon returning to it this afternoon I found that the new drive I added was marked as failed and everytime I try to re-add it using```
mdadm --re-add /dev/md0 /dev/sde
```I get a bunch of error messages saying "ata6 srst failed (errno=-16)" I have tried moving the drive to a different SATA port and that doesn't seem to fix it. I have also updated my BIOS and switched the SATA type from IDE to AHCI. Neither of these has fixed it. Right now I'm running a long SMART test to see if it's a DOA drive. 
Does anyone have any other ideas?

Also is there a way to get my RAID 5 back to just 3 drives without losing any of my data? This is just a home server so it doesn't need to be back up right away.

For information I'm currently running 10.04.3 x64 and the output of uname -a is ```
Linux *hostname* 2.6.32-33-server #72-Ubuntu SMP Fri Jul 29 21:21:55 UTC 2011 x86_64 GNU/Linux
```

Thanks

---

### Post by rubylaser on 2011-09-19
Sounds like a faulty drive or bad SATA cable.  A good practice is to always at a minimum write zeroes to a new disk and run a long SMART test before just throwing it into an array. That should weed out most DOA disks.  

Reducing the number of disks isn't super difficult, but you'll need a newer version of mdadm 3.1+ and I'll have to write up directions for you in a bit unless someone else beats me to it.
```
mdadm -V
```

---

### Post by littlegreiger on 2011-09-19
Thanks for the reply, I'll let you know what I get from the long SMART test and in the meantime I'm going to try to shrink the array using instructions like you posted in another thread [http://ubuntuforums.org/showthread.php?t=1794121]("http://ubuntuforums.org/showthread.php?t=1794121")
I guess I also need to get mdadm 3.x because I have 2.6.7.1
I'll post back if I need help with the shrink but for now you don't need to bother posting instructions.

---

### Post by rubylaser on 2011-09-20
Sounds like a plan. Here's how to upgrade mdadm...
```
sudo -i
```
**32 bit**
[CODE}wget http://ftp.us.debian.org/debian/pool/main/m/mdadm/mdadm_3.1.4-1+8efb9d1_i386.deb[/CODE]
**64 bit**
```
wget http://ftp.us.debian.org/debian/pool/main/m/mdadm/mdadm_3.1.4-1+8efb9d1_amd64.deb
```
```
dpkg -i mdadm*.deb
```
```
reboot
```

You  can try 3.2.2 if you'd like, but I prefer to stay on the well tested 3.1.4.

---

### Post by littlegreiger on 2011-09-20
Thanks, I actually upgraded to 3.1.4 using a ppa I found through google. The shrink seems to be working, takes a long time though, says something like another day or so, oh well.

As for the SMART test it finished and says there's no error and here's the output of "smartctl -a /dev/sdd" (I changed the SATA port hence sde becoming sdd)
```
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EARS-00J99B0
Serial Number:    WD-WCAWZ1166161
Firmware Version: 80.00A80
User Capacity:    2,000,398,934,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Sep 20 07:10:05 2011 MDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x80)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (42900) seconds.
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
  3 Spin_Up_Time            0x0027   229   175   021    Pre-fail  Always       -       5508
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       24
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       41
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       22
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       18
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       44
194 Temperature_Celsius     0x0022   109   099   000    Old_age   Always       -       43
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%        34         -
# 2  Short offline       Completed without error       00%        26         -

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

```So it looks like my drive isn't failing, but I'm still not sure I want to try to add it back to the array. Would zeroing it out help you think? I've never had to do that with other drives.

---

### Post by rubylaser on 2011-09-20
Resizing is going to take a while. Zeroing out wouldn't do anything other than map out bad sectors for you.  I'd do that, and once it's done, check dmesg for any entries about that device.
```
dmesg | grep sdd
```

Also, that is a 4K drive, did you properly [align the partitions]("http://ubuntuforums.org/showthread.php?t=1600517")?

---

### Post by littlegreiger on 2011-09-20
Well I tried zeroing out the drive using the following command```
sudo dd if=/dev/zero of=/dev/sdd
```and got this output```
dd: writing to `/dev/sdd': Input/output error
1060625+0 records in
1060624+0 records out
543039488 bytes (543 MB) copied, 121.064 s, 4.5 MB/s

```
The output of ```
dmesg | grep sdd
```returned a bunch of lines similar to```
66345.607192] sd 3:0:0:0: [sdd] Unhandled error code
[66345.607206] sd 3:0:0:0: [sdd] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[66345.607206] sd 3:0:0:0: [sdd] CDB: Write(10): 2a 00 00 05 38 38 00 04 00 00
[66345.607223] end_request: I/O error, dev sdd, sector 342072
[66345.609806] Buffer I/O error on device sdd, logical block 42759
``` I can't attach the output because it's too big apparently. 
*Edit: I've posted it to pastebin [http://pastebin.com/AHgPaz2i]("http://pastebin.com/AHgPaz2i")*

As for aligning partitions, I didn't do that with the other three I'm using and they worked fine. Also I'm using the entire device for the raid and it is not partitioned if that makes a difference.

---

