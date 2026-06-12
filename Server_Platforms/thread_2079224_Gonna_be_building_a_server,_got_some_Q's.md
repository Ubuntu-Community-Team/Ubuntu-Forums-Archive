---
title: "Gonna be building a server, got some Q's"
date: 2012-11-01
forum: Server Platforms
---

### Post by mallen324 on 2012-11-01
Hello all,

My backup server at work died (2 hard drive failures). It was on FreeBSD, so I am am taking this opportunity to get away from that OS (too different). As soon as I remake the RAID the on it, Im gonna be putting on Ubuntu Server. 

There will be about 40 users on it about 8 hours a day, and random people on it after hours. All of them use it as a file server (samba - windows desktops), half using it for smaller excel files, the other half using it for bigger (600 MB) SPSS files. 

Im thinking formatting the RAID to XFS. Does that sound like a good idea? And do you think RAID 5 would be good?

Ill probably pop back in this thread with more generic questions. Thanks for your time so far!

---

### Post by mallen324 on 2012-11-01
Well, rebuilding the array failed. I hoped it would tell me on which HDD(s). Anyone got some good suggestions on how to check which HDDs are bad?

Thanks!

---

### Post by CharlesA on 2012-11-01
Depends on what software the RAID was running on. I am pretty sure mdadm would tell you what drive failed, but you didn't say what software the array was built with.

---

### Post by thnewguy on 2012-11-01
I probably wouldn't use XFS as that file system seems to get a lot of corruption issues. I'd probably go with something more mainline like ext3 or ext4.

---

### Post by mallen324 on 2012-11-01
> **CharlesA said:**
> Depends on what software the RAID was running on. I am pretty sure mdadm would tell you what drive failed, but you didn't say what software the array was built with.

Real sorry about that. Not near the machine now. But I believe it is a 3ware RAID controller. Im gonna update this post as soon as I double check.

I guess I shoulda mentioned it was / is hardware RAID. Im trying to wipe the old raid array off now (again). hasnt failed yet, but we'll see.

---

### Post by mallen324 on 2012-11-01
> **thnewguy said:**
> I probably wouldn't use XFS as that file system seems to get a lot of corruption issues. I'd probably go with something more mainline like ext3 or ext4.

Thanks for your input thnewguy! What made me think I should use XFS was a user named sandyd in another thread had this to say:

> A few thoughts for the filesystem
XFS is good for storing large files. Since you have RAID5, XFS is fine because it can sometimes be intollerant of disk issues
JFS is good for storing small files, and has an extremely fast fsck, and will recover most damaged files.

Generally, the EXTx filesystem types are just 'general' filesystem types that work in both desktops and servers.

So I guess I could use the Extx format. Is it ok with files up to 700 MB getting accessed over a samba share (windows client)?

---

### Post by mallen324 on 2012-11-01
Just looked at the machine again. Doesnt say exactly what it is, but during boot up, I hit alt+3 to get to 3Ware BIOS Manager (doesnt say version or anything). I Deleted the array, gonna try and create the new array. 

Im making it raid 5 - only that, "single drive" and RAID 1 are available options. It has the option for 16, 64, or 256 striping. Im gonna google that value, but I think Ill keep it at the default 64 for now (unless you guys tell me otherwise). It also has Array's Write Cache State, either enabled or disabled. I have it enabled.

Should I even bother building this RAID array for now? Should I just boot up a live CD and test the HDDs that way when they are not in a raid? If so, would I use Ubuntu for that? Or something like GParted? 

Thanks for the help so far!

---

### Post by CharlesA on 2012-11-01
I've got files that are a couple gigs being stored on EXT4 on my file server at home.

From what I have heard, XFS should be fine tbh. I don't recall seeing anything about corruption with it.

---

### Post by rubylaser on 2012-11-01
Personally, I don't use XFS anymore (corruption issues in the past).  It's a stable filesystem if you don't ever have power issues (hooked up to a UPS). But, with so many other options that work well, I just don't use it anymore.  ext4 will work fine for your purposes.

Personally, I'd just hook the drives up without the controller, and then use smartmontools from the live Ubuntu CD to test them.

```
sudo -i
apt-get update && apt-get install smartmontools
smartctl -a /dev/sdb
```

Should give you output like this.
```
root@fileserver:~# smartctl -a /dev/sdb
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-32-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda Green (Adv. Format)
Device Model:     ST2000DL003-9VT166
Serial Number:    5YX5779C
LU WWN Device Id: 5 000c50 02f26b42b
Firmware Version: CC32
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Thu Nov  1 17:52:15 2012 EDT
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
data collection: 		(  623) seconds.
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
  1 Raw_Read_Error_Rate     0x000f   111   099   006    Pre-fail  Always       -       30221488
  3 Spin_Up_Time            0x0003   093   084   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   096   096   020    Old_age   Always       -       5064
 ** 5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0**
  7 Seek_Error_Rate         0x000f   075   060   030    Pre-fail  Always       -       38150194
  9 Power_On_Hours          0x0032   081   081   000    Old_age   Always       -       16995
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       70
183 Runtime_Bad_Block       0x0032   010   010   000    Old_age   Always       -       90
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   092   000    Old_age   Always       -       34360459279
189 High_Fly_Writes         0x003a   091   091   000    Old_age   Always       -       9
190 Airflow_Temperature_Cel 0x0022   076   058   045    Old_age   Always       -       24 (Min/Max 20/29)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       48
193 Load_Cycle_Count        0x0032   098   098   000    Old_age   Always       -       5095
194 Temperature_Celsius     0x0022   024   042   000    Old_age   Always       -       24 (0 18 0 0)
195 Hardware_ECC_Recovered  0x001a   020   008   000    Old_age   Always       -       30221488
**197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0**
**198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0**
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       222157183393581
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       2760009691
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       3125611782

SMART Error Log Version: 1
No Errors Logged
```

I've bolded some of the values you'll want to take a look at (numbers on the far right).

---

### Post by mallen324 on 2012-11-02
Thanks RUbyLaser! Gonna be doing that soon. Just downloading the ISOs now. I will update once I do.

---

### Post by SeijiSensei on 2012-11-02
Count me as another person who has had problems with XFS and power outages.  I gave up using it on an external hard drive because I would inevitably get file corruption problems if the power went out without warning.  Some years ago I used XFS on production machines with a solid backup power supply, but nowadays I just use ext4.

---

