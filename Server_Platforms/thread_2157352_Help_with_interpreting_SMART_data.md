---
title: "Help with interpreting SMART data"
date: 2013-06-25
forum: Server Platforms
---

### Post by CharlesA on 2013-06-25
Howdy,

I have been running 3 Hitachi DeskStar (DeathStar :p) drives in a RAID5 on my home server for a while now and recently added another drive to expand the array. In the end, I had to destroy the array and rebuild it with the new drive, but once that was done, it started "rebuilding" after the management software threw an error: "Array 'RAID5' data is not consistent."

That was on 6/21. Fast forward to today. The rebuilding completed with no errors and I have run a verify on the entire array with all 4 drives. No errors. No errors when accessing files that I am aware of and so far backups are up-to-date and good.

here's the SMART data:

```
	

    Drive 1:
    ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
[COLOR="#FF0000"]      1 Raw_Read_Error_Rate     0x000b   098   098   016    Pre-fail  Always       -       **262145**[/COLOR]
      2 Throughput_Performance  0x0005   134   134   054    Pre-fail  Offline      -       96
      3 Spin_Up_Time            0x0007   159   159   024    Pre-fail  Always       -       408 (Average 500)
      4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       186
      5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       20
      7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
      8 Seek_Time_Performance   0x0005   110   110   020    Pre-fail  Offline      -       40
      9 Power_On_Hours          0x0012   096   096   000    Old_age   Always       -       32532
     10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
     12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       186
    192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       969
    193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       969
    194 Temperature_Celsius     0x0002   162   162   000    Old_age   Always       -       37 (Min/Max 21/50)
    196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       20
    197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
    198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
[COLOR="#0000FF"]    199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0[/COLOR]
     
    Drive 2:
    ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
[COLOR="#FF0000"]      1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       **65536**[/COLOR]
      2 Throughput_Performance  0x0005   132   132   054    Pre-fail  Offline      -       106
      3 Spin_Up_Time            0x0007   151   151   024    Pre-fail  Always       -       436 (Average 522)
      4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       184
      5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       8
      7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
      8 Seek_Time_Performance   0x0005   112   112   020    Pre-fail  Offline      -       39
      9 Power_On_Hours          0x0012   096   096   000    Old_age   Always       -       32536
     10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
     12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       184
    192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       950
    193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       950
    194 Temperature_Celsius     0x0002   150   150   000    Old_age   Always       -       40 (Min/Max 22/50)
    196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       11
    197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
    198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
[COLOR="#0000FF"]    199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0[/COLOR]
     
    Drive 3:
    ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
[COLOR="#FF0000"]      1 Raw_Read_Error_Rate     0x000b   098   098   016    Pre-fail  Always       -       5[/COLOR]
      2 Throughput_Performance  0x0005   133   133   054    Pre-fail  Offline      -       101
      3 Spin_Up_Time            0x0007   150   150   024    Pre-fail  Always       -       439 (Average 524)
      4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       184
      5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       3
      7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
      8 Seek_Time_Performance   0x0005   112   112   020    Pre-fail  Offline      -       39
      9 Power_On_Hours          0x0012   096   096   000    Old_age   Always       -       32532
     10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
     12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       184
    192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       998
    193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       998
    194 Temperature_Celsius     0x0002   153   153   000    Old_age   Always       -       39 (Min/Max 22/54)
    196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       4
    197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
    198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
[COLOR="#0000FF"]    199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0[/COLOR]
     
    Drive 4:
    ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
[COLOR="#FF0000"]      1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0[/COLOR]
      2 Throughput_Performance  0x0005   133   133   054    Pre-fail  Offline      -       99
      3 Spin_Up_Time            0x0007   169   169   024    Pre-fail  Always       -       440 (Average 416)
      4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       10
      5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
      7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
      8 Seek_Time_Performance   0x0005   121   121   020    Pre-fail  Offline      -       35
      9 Power_On_Hours          0x0012   100   100   000    Old_age   Always       -       201
     10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
     12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       10
    192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       12
    193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       12
    194 Temperature_Celsius     0x0002   166   166   000    Old_age   Always       -       36 (Min/Max 25/44)
    196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
    197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
    198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
[COLOR="#0000FF"]    199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0[/COLOR]


```

Now, I have read a [couple]("http://hardforum.com/showthread.php?t=1583604") [different]("http://lime-technology.com/forum/index.php?topic=14504.0") threads about how these read error and UDMA CRC errors are not necessarily saying the drive is going out, but that the cable might be going bad or is lose. So far I have reseated the cable on all the drives, but I have not replaced them.

Can I get some opinions on this? In the past I have only really been keeping an eye on Reallocated_Sector_Ct, Reallocated_Event_Count, Current_Pending_Sector, and Offline_Uncorrectable because I read those were the important things to keep an eye on on [wikipedia]("http://en.wikipedia.org/wiki/S.M.A.R.T.") (insert lulz here).

Anyway, up until this totally random rebuild on the 21st, I haven't had any issues with the array since I put it into place. It has been moved from my old server running 10.04, to a new server running 12.04 and now Debian 7.0 with no issues. I only started having problems when I added another drive. I have been running a verify every two weeks and those have caught the current bad sectors. I'm now thinking of setting it up to run a verify every week and then to do a smart test before emailing me the results, so I can keep an eye on them.

Here's the main reason for this post: Should I be worried about replacing the two drives with a high raw_rear_error_count, or leave them be as I have yet to run into problems and I have good backups?

I currently have 1 spare 2TB drive that I can replace one of the drives with, but I would need to order another one to get everything "in the green" again. Thoughts?

Thanks in advance.

EDIT: With all that being said, I am seeing similar things on both my OS drive and the external backup drive, but so far it seems like it is a [Seagate thing]("http://forums.seagate.com/t5/Barracuda-XT-Barracuda-Barracuda/Seagate-s-Seek-Error-Rate-Raw-Read-Error-Rate-and-Hardware-ECC/td-p/122382"). Any opinions would be welcome.

```
OS Drive:
=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.12
Device Model:     ST3500418AS
Serial Number:    9VM6WZ62
LU WWN Device Id: 5 000c50 019f6e395
Firmware Version: CC38
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   117   099   006    Pre-fail  Always       -       143554816
  3 Spin_Up_Time            0x0003   097   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       175
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   077   060   030    Pre-fail  Always       -       56698229
  9 Power_On_Hours          0x0032   076   076   000    Old_age   Always       -       21786
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       87
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   096   000    Old_age   Always       -       157
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   069   056   045    Old_age   Always       -       31 (Min/Max 28/33)
194 Temperature_Celsius     0x0022   031   044   000    Old_age   Always       -       31 (0 21 0 0)
195 Hardware_ECC_Recovered  0x001a   034   024   000    Old_age   Always       -       143554816
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       105398497465792
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       465972698
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       4216579979

External backup drive:
=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda XT
Device Model:     ST33000651AS
Serial Number:    9XK06WXD
LU WWN Device Id: 5 000c50 02d0a77dd
Firmware Version: CC43
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Size:      512 bytes logical/physical
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   115   099   006    Pre-fail  Always       -       84433708
  3 Spin_Up_Time            0x0003   089   089   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       546
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   072   060   030    Pre-fail  Always       -       18697178
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       870
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       17
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   095   095   000    Old_age   Always       -       5
190 Airflow_Temperature_Cel 0x0022   038   028   045    Old_age   Always   FAILING_NOW 62 (0 47 67 31)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       9
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       1027
194 Temperature_Celsius     0x0022   062   072   000    Old_age   Always       -       62 (0 15 0 0)
195 Hardware_ECC_Recovered  0x001a   019   009   000    Old_age   Always       -       281470766177068
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       82046760256032
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       4092398426
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       3580989180
```

---

### Post by TheFu on 2013-06-25
According to all my reading, SMART data is next to worthless for predicting disk failures.  The only SMART data that seems to be of use is when the disk subsystem gets a warning that a HDD is about to fail.

I'm with you on backups and I've pre-emptively replaced very old HDDs in an array in the last 6 months.  I asked on my blog how long do people use HDDs? [http://blog.jdpfu.com/2012/08/20/how-long-do-you-use-hard-drives](http://blog.jdpfu.com/2012/08/20/how-long-do-you-use-hard-drives)

The key that we know is to "replace every HDD just before it fails."  Not much help, I know.

---

### Post by CharlesA on 2013-06-25
Thanks for the input. That's pretty much what I've come to the conclusion on, too. Most of the stuff I have seen has been "Well, the drive could be failing, but have you tried it in another machine?"

So far the array is working well. The verify completed with no problems and from what I can tell, there has been no read errors. The verify would have picked up on that wouldn't it?

I'm thinking of just running with the drives I have now until SMART shows a "FAIL." That might not be the smartest thing to do, but it's a home server and I have it set up to backup via CrashPlan every 15 minutes and backup to external media daily, so I wouldn't be losing data in the event more than one drive goes out.

Do you have any experience with those new WD Red drives? I'm thinking if/when I get around to replacing the disks, I'll replace the RAID card and/or start using mdadm at the same time.

---

### Post by TheFu on 2013-06-25
> **CharlesA said:**
> Do you have any experience with those new WD Red drives? I'm thinking if/when I get around to replacing the disks, I'll replace the RAID card and/or start using mdadm at the same time.

I **knew** you'd have a solid backup method.

Yes, my old array holds 4 drives - 2 are WD-Red drives. Added those about 2-3 months ago.  As far as I can tell, there hasn't been any difference between those or the Seagates mentioned in the blog article.  In theory, non-Black and non-Red HDDs should have issues when put into a RAID set.  I'm not seeing that, but time will prove ... at least for my environment.
```

md2 : active raid1 sdf2[1] sde2[0]
      1338985536 blocks [2/2] [UU]
      
md1 : active raid1 sdc3[0] sdd3[1]
      1943010816 blocks super 1.2 [2/2] [UU]

```
I do weekly **mdadm verify** runs on each array just after backups, but still very early in the morning.  So far, nothing bad has been reported.

I haven't run disk performance tests with these new drives, but I did tune the read-ahead values for both the individual disks AND the array after testing.  Also went with a larger array stripe (256) that my old-school docs suggested (64/128). The box running this storage is a Core i5 with plenty of RAM and multiple GigE NICs.

BTW, I was burned by a RAID card a few years ago and couldn't get a replacement for anything less than 4x the cost. Switched to software-RAID and never looked back.  I've moved the disk array between 3 different systems, never lost any data.  Performance is not great, but I can't tell where the slowdown is. It is more than fast enough for my long running batch jobs.

---

### Post by CharlesA on 2013-06-25
> **TheFu said:**
> I **knew** you'd have a solid backup method.

Guess I am a bit insane when it comes to making sure I have backups of my data. I've lost data a few times before, mostly from bad CDs and ZIP disks and *gasp* floppy disks but so far I've had no issues when I moved to using HDD to back stuff up.

> Also went with a larger array stripe (256) that my old-school docs suggested (64/128). The box running this storage is a Core i5 with plenty of RAM and multiple GigE NICs.

What are the benefits of using a larger stripe? My array defaulted to a 64K stripe (I think it's the stripe... the management software calls it "block size")

> BTW, I was burned by a RAID card a few years ago and couldn't get a replacement for anything less than 4x the cost. Switched to software-RAID and never looked back.  I've moved the disk array between 3 different systems, never lost any data.  Performance is not great, but I can't tell where the slowdown is. It is more than fast enough for my long running batch jobs.

That is one of my worries as well, but not a huge one as I am totally anal about backups. Of course that might also be cuz I'm running a super cheap RAID card and I could just restore from backups if the card went out and a replacement didn't see the array.

I'm really considering software RAID, even though I originally went for hardware RAID cuz it was supposedly faster, but so far it has been a pain in the butt. The card I have (RocketRaid 2640x1) needs a proprietary drivers and I've had issues with it compiling correctly via DKMS. The management software is pretty basic and doesn't give you as much info from SMART as I would like, but it works. The funny thing is I didn't want to use mdadm because it looked super complex to me but that was also 3-4 years ago and I've learned a lot since then. :lolflag:

---

### Post by rubylaser on 2013-06-25
> **CharlesA said:**
> What are the benefits of using a larger stripe? My array defaulted to a 64K stripe (I think it's the stripe... the management software calls it "block size")
64k chunk size is fine.  That is a good value, and is the default for a reason.  Going with a larger chunk size can be beneficial if you are dealing primarily with large, sequential reads.  

Also, I wouldn't say SMART data is completely worthless. If you setup smartmontools to monitor and test your disks periodically (with email alerts setup), they can be a decent early warning system.  If values start increasing, this can be an indicator of a pre-fail.  SMART data will never give you a definitive alert like,  *"This disk is going to fail tomorrow"*, but if you monitor your disks, you can often see a failing disk (and replace it) prior to it actually failing.

---

### Post by CharlesA on 2013-06-25
I was just looking at your blog post on mdadm... :)

I totally agree with you there. So far I have had a script setup to check the SMART data every week on Sunday morning and having the software do a verify every two weeks and haven't run into any issues. I still have the full smart logs instead of the snipped down logs I get via email, so I can look them over if I feel like it.

Thanks for helping clear up some of my confusion.

EDIT: I looked thru my logs from 6/3/12 and found that RAID#1 was sitting at a Raw_Read_Error_Rate of 26144:

```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   098   098   016    Pre-fail  Always       -       262144
  2 Throughput_Performance  0x0005   134   134   054    Pre-fail  Offline      -       97
  3 Spin_Up_Time            0x0007   141   141   024    Pre-fail  Always       -       477 (Average 545)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       174
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   110   110   020    Pre-fail  Offline      -       40
  9 Power_On_Hours          0x0012   097   097   000    Old_age   Always       -       23255
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       174
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       884
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       884
194 Temperature_Celsius     0x0002   187   187   000    Old_age   Always       -       32 (Min/Max 21/50)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0

```

RAID#2:
```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   131   131   054    Pre-fail  Offline      -       107
  3 Spin_Up_Time            0x0007   151   151   024    Pre-fail  Always       -       395 (Average 560)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       172
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       8
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   112   112   020    Pre-fail  Offline      -       39
  9 Power_On_Hours          0x0012   097   097   000    Old_age   Always       -       23258
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       172
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       872
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       872
194 Temperature_Celsius     0x0002   181   181   000    Old_age   Always       -       33 (Min/Max 22/50)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       11
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0

```

Raid#3:
```

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   094   094   016    Pre-fail  Always       -       65555
  2 Throughput_Performance  0x0005   132   132   054    Pre-fail  Offline      -       103
  3 Spin_Up_Time            0x0007   151   151   024    Pre-fail  Always       -       395 (Average 563)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       172
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       3
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   107   107   020    Pre-fail  Offline      -       41
  9 Power_On_Hours          0x0012   097   097   000    Old_age   Always       -       23255
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       172
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       901
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       901
194 Temperature_Celsius     0x0002   187   187   000    Old_age   Always       -       32 (Min/Max 22/54)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       3
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0

```

RAID #3 makes me go lolwut.

---

### Post by rubylaser on 2013-06-25
I hope that mdadm article helps you out. I love mdadm and still use it at work everyday, but for my home use, I've actually switched over to [SnapRAID]("http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04") for my media storage and ZFS (raidz2) for all my really important stuff.  I still backup to my collocated fileserver and to Amazon Glacier for my irreplaceable stuff (pictures, home movie, and documents).

Also, my Seagate drives have always had ridiculously high Raw_Read_Error_Rates as well.  Here are two of my Seagate drives. Both of these drives are healthy and work great.
```

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   114   097   006    Pre-fail  Always       -       73247840
  3 Spin_Up_Time            0x0003   093   074   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   098   098   020    Old_age   Always       -       2190
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   058   056   030    Pre-fail  Always       -       283516086817
  9 Power_On_Hours          0x0032   080   080   000    Old_age   Always       -       17969
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       95
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       477
188 Command_Timeout         0x0032   100   092   000    Old_age   Always       -       4295032858
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   077   062   045    Old_age   Always       -       23 (Min/Max 21/31)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       81
193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       3499
194 Temperature_Celsius     0x0022   023   040   000    Old_age   Always       -       23 (0 16 0 0)
195 Hardware_ECC_Recovered  0x001a   024   007   000    Old_age   Always       -       73247840
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       216603790677821
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       494625907
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       491619127

```
```

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   118   099   006    Pre-fail  Always       -       194365396
  3 Spin_Up_Time            0x0003   100   100   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   097   097   020    Old_age   Always       -       3338
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   072   060   030    Pre-fail  Always       -       8621789498
  9 Power_On_Hours          0x0032   083   083   000    Old_age   Always       -       15641
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       58
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   086   000    Old_age   Always       -       68720787483
189 High_Fly_Writes         0x003a   095   095   000    Old_age   Always       -       5
190 Airflow_Temperature_Cel 0x0022   071   060   045    Old_age   Always       -       29 (Min/Max 20/33)
194 Temperature_Celsius     0x0022   029   040   000    Old_age   Always       -       29 (0 15 0 0)
195 Hardware_ECC_Recovered  0x001a   040   022   000    Old_age   Always       -       194365396
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       240951960288185
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       1527605445
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       3684894397

```

---

### Post by CharlesA on 2013-06-25
SnapRAID is actually pretty cool. It looks very similar to the setup for mdadm. Do you use it for storage only or for other stuff too? I'm currently using my array to handle storage for my VMs via KVM and OpenVZ.

I wonder if it could work with LVM. At first glance, I doubt it because the drives are pooled, but maybe.

Good to know my drives aren't the only ones that are kinda screwy. You would think there would be some standard for SMART.. but nope.

EDIT: The reason I am asking is because I am currently running Debian Wheezy with Proxmox on top of it on my server. LVM snapshots for backups sound handy.

---

### Post by rubylaser on 2013-06-25
You could use SnapRAID for VMs, but that's not what it's designed for. SnapRAID is primarily for storage that doesn't change that often (movies, tv shows, pictures, etc.).  Also, SnapRAID doesn't pool by itself, it's an option, but I don't cover it in my tutorial. I use AUFS to pool the disks. 

I also use Proxmox (at home, work, and for sites I host for others at the datacenter).  I use my ZFS array with an ISCSI share to Proxmox at home and at the datacenter, I use hardware LSI RAID cards for my (4) Proxmox hosts and then backup to a (10) drive mdadm RAID6 array.  Both of these methods have worked very well for me.

---

### Post by CharlesA on 2013-06-25
Nice. Thanks for the info. I've seen some pretty decent LSI cards on ebay, and they look a hell of a lot better than the card I am using now.

What LSI cards are you using on your Proxmox hosts? And did you have to do anything special to get them to be recognized by the OS?

---

### Post by rubylaser on 2013-06-25
I'm using a mix of (2) LSI [9260-4i]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816118106") and and (2) [9260-8i]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816118104")'s.  They are expensive, but my brother-in-law got them for a great price through work (we both use this Proxmox cluster for our clients and personal stuff).  There is nothing that needs to be done to the OS to have them recognized, they just work. LSI makes many, cheaper options than these that work well too. 
 
The [Proxmox wiki]("http://pve.proxmox.com/wiki/Raid_controller") has a small segment of suggested RAID cards. Another card that is cheap the [works okay]("http://forum.proxmox.com/threads/10351-HP-DL380-G5-RAID-Status"), is the [HP P400]("http://www.ebay.com/itm/411064-B21-HP-P400i-512mb-BBWC-SMART-ARRAY-CONTROLLER-W-BATTERY-AND-CABLE-/261215716472?pt=US_Server_Disk_Controllers_RAID_Cards&hash=item3cd1ab8478") series.

---

### Post by CharlesA on 2013-06-25
Huh. I just saw a [9240-4i]("http://www.ebay.com/itm/LSI-Internal-SATA-SAS-MegaRAID-9240-4i-6Gb-s-PCIe-2-0-RAID-Controller-With-Cable-/330943229587?pt=US_Server_Disk_Controllers_RAID_Cards&hash=item4d0dc0ee93") used for 60 bucks. I'd probably still use it for RAID5 with 4 drives, but because it is a SATA3 card, I can always expand to using 4 x 3TB drives.

That sounds like a hell of a deal to me, even if it is used.

Now my only thing is that it is ebay...

EDIT: I found a [8 drive one]("http://www.ebay.com/itm/NEW-LSI-MegaRAID-9240-8i-8-port-PCI-Express-6Gb-s-SATA-SAS-RAID-controller-Card-/151066550887?pt=US_Server_Disk_Controllers_RAID_Cards&hash=item232c44a267"), but it's way more expensive and has no cables..

---

### Post by tgalati4 on 2013-06-25
As far as your original problem, I would suspect a sagging power supply.  When you add another disk to a working array and the array starts to show issues, it could simply be too much current draw as all the drives try to spin up at once.  That would account for raw read errors (the disks haven't spun up to speed completely) but otherwise OK read and write performance.  Put a meter on your PSU and watch for voltage drops on the 12VDC rail during bootup.  A 10% drop (10.8VDC) could be an issue, although I think server specifications are no more than 5% drop (11.4VDC).

---

### Post by CharlesA on 2013-06-25
> **tgalati4 said:**
> As far as your original problem, I would suspect a sagging power supply.  When you add another disk to a working array and the array starts to show issues, it could simply be too much current draw as all the drives try to spin up at once.  That would account for raw read errors (the disks haven't spun up to speed completely) but otherwise OK read and write performance.  Put a meter on your PSU and watch for voltage drops on the 12VDC rail during bootup.  A 10% drop (10.8VDC) could be an issue, although I think server specifications are no more than 5% drop (11.4VDC).

Thanks for the tip. It's running an OCZ 750W PSU, which probably isn't the best out there. Where would you recommend measuring the 12V rail from?

---

### Post by rubylaser on 2013-06-26
Do you know the model number?  A 750W PSU from OCZ should be massive overkill for running only 4 hard drives.  My SnapRAID fileserver has (9) hard drives in it running off a Coolermaster 650 Watt PSU, but it's a single rail model.

---

### Post by rubylaser on 2013-06-26
Also, the 9260-4i @ $60 is a great deal.  You just need to add a [SFF-8087 cable]("http://www.monoprice.com/products/product.asp?c_id=102&cp_id=10254&cs_id=1025406&p_id=8186&seq=1&format=2"), and you are ready to go.

---

### Post by CharlesA on 2013-06-26
> **rubylaser said:**
> Do you know the model number?  A 750W PSU from OCZ should be massive overkill for running only 4 hard drives.  My SnapRAID fileserver has (9) hard drives in it running off a Coolermaster 650 Watt PSU, but it's a single rail model.

It's this one:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817341052](http://www.newegg.com/Product/Product.aspx?Item=N82E16817341052)
Single 12V rail @ 62Amps.

> **rubylaser said:**
> Also, the 9260-4i @ $60 is a great deal.  You just need to add a [SFF-8087 cable]("http://www.monoprice.com/products/product.asp?c_id=102&cp_id=10254&cs_id=1025406&p_id=8186&seq=1&format=2"), and you are ready to go.

My mistake it looks like it was a 9240-4i @ $60 and my edit didn't take. The only difference I saw between the two card was the 9240 supported RAID 0, 1, 5 while the 9260 supported RAID 0,1, 5, 6. Dunno if there are any other major differences though.

I did find a [9260-4i]("http://www.ebay.com/itm/New-LSI-MegaRAID-SAS-LSI9260-4i-4-port-6Gb-s-PCI-Express-RAID-Controller-Kit-/271219067486?pt=US_Computer_Disk_Controllers_RAID_Cards&hash=item3f25ea8a5e") new for almost $300 coming from California, which seems like an ok deal considering the one at Newegg is $320. Funny thing is I found a refurbished [9260-8i]("http://www.ebay.com/itm/LSI-MegaRAID-SAS-9260-8i-512MB-6GB-SAS-Full-HeightBracket-with-IBM-M5015-battery-/151068843013?pt=US_Server_Disk_Controllers_RAID_Cards&hash=item232c679c05") for a little bit more than the 4i. Granted it is coming from Taiwan and is refurbished, it does have a BBU... which my current card doesn't have. Would the cables at monoprice work for it too?

---

### Post by rubylaser on 2013-06-26
> **CharlesA said:**
> It's this one:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817341052](http://www.newegg.com/Product/Product.aspx?Item=N82E16817341052)
Single 12V rail @ 62Amps.

My mistake it looks like it was a 9240-4i @ $60 and my edit didn't take. The only difference I saw between the two card was the 9240 supported RAID 0, 1, 5 while the 9260 supported RAID 0,1, 5, 6. Dunno if there are any other major differences though.

Unless there is something wrong with your PSU, that one is certainly more than up to the task you are using it for.  The 9240-4i doesn't have onboard cache, so write speeds will be terrible, so I would avoid that one. 
 
Also, the SFF-8087 cable I supplied you with will work fine with any of those LSI cards. The HP P400i card that I mentioned earlier uses a [SFF-8484 cable]("http://www.newegg.com/Product/Product.aspx?Item=N82E16812228053&nm_mc=KNC-GoogleAdwords&cm_mmc=KNC-GoogleAdwords-_-pla-_-SCSI+%2f+SAS+%2f+InfiniBand+Cables-_-N82E16812228053&gclid=CLjsrsHMgbgCFe3m7Aod1D8Aaw") though.

---

### Post by CharlesA on 2013-06-26
> **rubylaser said:**
> Unless there is something wrong with your PSU, that one is certainly more than up to the task you are using it for.  The 9240-4i doesn't have onboard cache, so write speeds will be terrible, so I would avoid that one. 
 
Also, the SFF-8087 cable I supplied you with will work fine with any of those LSI cards. The HP P400i card that I mentioned earlier uses a [SFF-8484 cable]("http://www.newegg.com/Product/Product.aspx?Item=N82E16812228053&nm_mc=KNC-GoogleAdwords&cm_mmc=KNC-GoogleAdwords-_-pla-_-SCSI+%2f+SAS+%2f+InfiniBand+Cables-_-N82E16812228053&gclid=CLjsrsHMgbgCFe3m7Aod1D8Aaw") though.

Oh yikes, that would be a bad thing, especially if you need a lot of throughput. I just checked on my [current (cheap) RAID card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816115053") and it doesn't appear to have any cache on it either, but they did recommend getting a BBU with it.

I wonder if that is why my IO wait gets so high if I am doing multiple things at the same time - restoring a snapshot and transferring files or the like.

---

### Post by rubylaser on 2013-06-26
Yeah for roughly $120, you are not going to be able to get a great performing hardware RAID card, unless you are buying used :)  There is no cache on your card, so a BBU won't really help because there is no cached writes to protect.

---

### Post by CharlesA on 2013-06-26
> **rubylaser said:**
> Yeah for roughly $120, you are not going to be able to get a great performing hardware RAID card, unless you are buying used :)  There is no cache on your card, so a BBU won't really help because there is no cached writes to protect.

Funny, the manual mentioned stuff about recommending a BBU, but I guess that is just to cover themselves in case someone loses data after a power failure.

Thanks for the info. It's surprising how much you learn over the years.

---

### Post by CharlesA on 2013-07-08
Bumping this cuz I just had my first encounter with 9 (!) URE's around 12 days after I did an extended offline test of that drive. I was doing a consistency check on the newly built RAID6 array when I got back-to-back notifications about this. I guess it does pay to get a good card if you are going to run hardware RAID. :p

The only indication that the drive was having problem were a few bad sectors from a year or more ago. No raw read errors or anything. I have a feeling that might have been what caused the rebuild a couple weeks back, but since I have no notification of what actually caused the rebuild other then the "data is not consistent" error, I guess I'll never know.

Here's the current SMART data - don't mind the 45c temp reading as the server is sitting in my room and it's hot as hell in here.

```
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-2.6.32-20-pve] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

/dev/sda [megaraid_disk_16] [SAT]: Device open changed type from 'megaraid' to 'sat'
=== START OF INFORMATION SECTION ===
Model Family:     Hitachi Deskstar 7K2000
Device Model:     Hitachi HDS722020ALA330
Serial Number:    JK1120YAG26EUP
LU WWN Device Id: 5 000cca 221c100f0
Firmware Version: JKAOA20N
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Sun Jul  7 22:13:54 2013 PDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
Warning: This result is based on an Attribute check.

General SMART Values:
Offline data collection status:  (0x84)	Offline data collection activity
					was suspended by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(22477) seconds.
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
recommended polling time: 	 ( 255) minutes.
SCT capabilities: 	       (0x003d)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   133   133   054    Pre-fail  Offline      -       101
  3 Spin_Up_Time            0x0007   127   127   024    Pre-fail  Always       -       621 (Average 513)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       195
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       3
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   112   112   020    Pre-fail  Offline      -       39
  9 Power_On_Hours          0x0012   096   096   000    Old_age   Always       -       32840
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       195
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       1013
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       1013
194 Temperature_Celsius     0x0002   125   125   000    Old_age   Always       -       48 (Min/Max 22/54)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       4
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 9 (device log contains only the most recent five errors)
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

Error 9 occurred at disk power-on lifetime: 32839 hours (1368 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 02 1d 2c ee 00  Error: UNC at LBA = 0x00ee2c1d = 15608861

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 02 00 1d 2c ee 40 00      06:16:35.124  READ FPDMA QUEUED
  61 00 80 00 a6 b0 40 00      06:16:32.935  WRITE FPDMA QUEUED
  61 00 78 00 a4 b0 40 00      06:16:32.935  WRITE FPDMA QUEUED
  61 00 70 00 a2 b0 40 00      06:16:32.934  WRITE FPDMA QUEUED
  61 00 68 00 a0 b0 40 00      06:16:32.934  WRITE FPDMA QUEUED

Error 8 occurred at disk power-on lifetime: 32839 hours (1368 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 e1 1f 2c ee 00  Error: WP at LBA = 0x00ee2c1f = 15608863

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 00 78 00 84 b0 40 00      06:16:12.165  WRITE FPDMA QUEUED
  61 00 f8 00 82 b0 40 00      06:16:12.158  WRITE FPDMA QUEUED
  61 00 70 00 80 b0 40 00      06:16:12.151  WRITE FPDMA QUEUED
  61 00 68 00 7e b0 40 00      06:16:12.144  WRITE FPDMA QUEUED
  61 00 60 00 7c b0 40 00      06:16:12.133  WRITE FPDMA QUEUED

Error 7 occurred at disk power-on lifetime: 32839 hours (1368 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 e4 1c 2c ee 00  Error: WP at LBA = 0x00ee2c1c = 15608860

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 00 a0 00 04 b0 40 00      06:15:52.662  WRITE FPDMA QUEUED
  61 00 98 00 02 b0 40 00      06:15:52.648  WRITE FPDMA QUEUED
  61 00 90 00 00 b0 40 00      06:15:52.633  WRITE FPDMA QUEUED
  61 00 88 00 fe af 40 00      06:15:52.612  WRITE FPDMA QUEUED
  61 00 78 00 fc af 40 00      06:15:52.598  WRITE FPDMA QUEUED

Error 6 occurred at disk power-on lifetime: 32839 hours (1368 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 e5 1b 2c ee 00  Error: UNC at LBA = 0x00ee2c1b = 15608859

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 e6 00 1a 2c ee 40 00      06:15:32.604  READ FPDMA QUEUED
  60 d0 00 00 44 d7 40 00      06:15:32.486  READ FPDMA QUEUED
  2f 00 01 10 00 00 00 00      06:15:32.097  READ LOG EXT
  60 d0 00 00 44 d7 40 00      06:15:27.100  READ FPDMA QUEUED
  60 e7 28 19 2c ee 40 00      06:15:15.002  READ FPDMA QUEUED

Error 5 occurred at disk power-on lifetime: 32839 hours (1368 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 e7 19 2c ee 00  Error: UNC at LBA = 0x00ee2c19 = 15608857

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 d0 00 00 44 d7 40 00      06:15:27.100  READ FPDMA QUEUED
  60 e7 28 19 2c ee 40 00      06:15:15.002  READ FPDMA QUEUED
  61 78 20 08 5a 95 40 00      06:15:15.001  WRITE FPDMA QUEUED
  61 08 18 00 1a a8 40 00      06:15:15.001  WRITE FPDMA QUEUED
  61 08 10 00 5a 9d 40 00      06:15:15.001  WRITE FPDMA QUEUED

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     32535         -
# 2  Short offline       Completed without error       00%     32459         -

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

EDIT:
> **tgalati4 said:**
> As far as your original problem, I would suspect a sagging power supply.  When you add another disk to a working array and the array starts to show issues, it could simply be too much current draw as all the drives try to spin up at once.  That would account for raw read errors (the disks haven't spun up to speed completely) but otherwise OK read and write performance.  Put a meter on your PSU and watch for voltage drops on the 12VDC rail during bootup.  A 10% drop (10.8VDC) could be an issue, although I think server specifications are no more than 5% drop (11.4VDC).

I just tested the 12V rail with a DMM, it was reading 12.25V - 12.27V from the time I hit the power button to the time the machine was fully booted. 10% of 12V would be 1.2V, and 5% would be 0.6V, so it looks to be within 2.5% tolerance.

All drives are set to spin up at the same time, so I guess that means power is good. :)

---

### Post by rubylaser on 2013-07-08
Charles, are you seeing this behavior on any of your other disks attached to the same SFF-8087 cable?  I ask because these [COLOR=#000000][FONT=Ubuntu Mono]WRITE FPDMA QUEUED [/FONT][/COLOR]errors are typically caused by either a SATA cable/connection or a power issue (loose cable, backplane issue, bad splitter, etc).  You have a lot of new pieces in your server: new RAID card, new cables, and hard drive dock, so I wouldn't immediately say this disk is bad.  Also, I would try to find a cooler place to run that server, 45c is really hot for a modern hard drive.

---

### Post by CharlesA on 2013-07-08
All the other disks are fine. I'll be moving it back to the other room where it's a bit cooler.

The funny thing is the drive running on the internal drive bays is running at around 7C cooler than the ones in the dock. I'm guessing that is due to there being a 120mm fan on the front panel vs an 80mm fan on the drive cage.

EDIT: I wonder if I should replace the 80mm fan with something with more CFM, but I dunno.

---

### Post by rubylaser on 2013-07-08
> **CharlesA said:**
> All the other disks are fine. I'll be moving it back to the other room where it's a bit cooler.

The funny thing is the drive running on the internal drive bays is running at around 7C cooler than the ones in the dock. I'm guessing that is due to there being a 120mm fan on the front panel vs an 80mm fan on the drive cage.

EDIT: I wonder if I should replace the 80mm fan with something with more CFM, but I dunno.

That's good to hear.  If all other disks are not showing any errors, that does point at this disk.  Also, I don't have that version of the Icy Dock enclosure (mine is older), but mine has kept my drives within the same temperature range as those inside the case.  

Here is one from from inside the Icy Dock enclosure.
```
root@fileserver:~# smartctl -a /dev/sdb | grep Temp
194 Temperature_Celsius     0x0022   025   040   000    Old_age   Always       -       25 (0 16 0 0)
```
and one inside the case with a 120mm in front of it.
```
root@fileserver:~# smartctl -a /dev/sdf | grep Temp
194 Temperature_Celsius     0x0002   230   230   000    Old_age   Always       -       26 (Min/Max 16/39)
```

---

### Post by CharlesA on 2013-07-08
Nice. What's the ambient temperature?

The ambient temperature is current around 84F = 28C. It should keep things around that temperature. :(

I just ordered 6 of [these]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822236521") drives. The intention being to run 5 of them in RAID6 with 1 as a hot spare.

I opened the case up and it looks like a SATA power cable might have been touching the fan... which would explain the heat buildup.

---

### Post by rubylaser on 2013-07-08
> **CharlesA said:**
> Nice. What's the ambient temperature?

The ambient temperature is current around 84F = 28C. It should keep things around that temperature. :(

I just ordered 6 of [these]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822236521") drives. The intention being to run 5 of them in RAID6 with 1 as a hot spare.

I opened the case up and it looks like a SATA power cable might have been touching the fan... which would explain the heat buildup.

The ambient temperature in my basement is 70F or ~21.1C, so mine are warmer than ambient by 4-5C. I'm all for data security, but with only (6) spindles, I would feel fine running without a hot spare (unless space isn't an issue at all).  That should be a nice, large, and safe storage volume.  Now, I just need to have my own Congressional approval (wife) to be able to green light buying 6 disks at once :)

---

### Post by CharlesA on 2013-07-08
> **rubylaser said:**
> The ambient temperature in my basement is 70F or ~21.1C, so mine are warmer than ambient by 4-5C. I'm all for data security, but with only (6) spindles, I would feel fine running without a hot spare (unless space isn't an issue at all).  That should be a nice, large, and safe storage volume.  Now, I just need to have my own Congressional approval (wife) to be able to green light buying 6 disks at once :)

My credit card weeps. :p

Thanks for the info about the hot spare. My logic on having one was to give the array the ability to rebuild should a drive fail and run off the spare drive while I RMA the bad one.

I dunno if that logic is actually sound or not, but those were my thought processes.

I just redid all the cable management and routed stuff away from fans, but now one drive doesn't want to come up (it's drive #1), which didn't show any errors at all.

Guess I get to troubleshoot the drives and the new drive cage... *sigh*

---

### Post by rubylaser on 2013-07-08
Take a photo of the case and setup.  I'd love to see how it all turned out :)  Sorry to hear about the drive not coming up, but I'm sure you'll figure it out.  And, 1 hot spare is a great idea from a data security standpoint + you can always still add (2) more drives down the line if you need extra space.

---

### Post by CharlesA on 2013-07-08
> **rubylaser said:**
> Take a photo of the case and setup.  I'd love to see how it all turned out :)  Sorry to hear about the drive not coming up, but I'm sure you'll figure it out.  And, 1 hot spare is a great idea from a data security standpoint + you can always still add (2) more drives down the line if you need extra space.

I'll post some pictures after I get some lunch.

I hooked the drives up outside the drive cage and all five of them loaded up, so it looks like that one or two slots on the drive cage are toast.

What a pain. :(

---

### Post by rubylaser on 2013-07-08
That is a pain.  It almost takes the enjoyment out of new hardware... *almost* ;)  Make sure that your power cables are really seated well into the dock.  That's one reason I like mine with the old 4 pin Molex connectors, it's very obvious when they are connected.

---

### Post by CharlesA on 2013-07-08
> **rubylaser said:**
> That is a pain.  It almost takes the enjoyment out of new hardware... *almost* ;)  Make sure that your power cables are really seated well into the dock.  That's one reason I like mine with the old 4 pin Molex connectors, it's very obvious when they are connected.

Indeed. Those molex buggers are a pain to unplug. ;)

The nice thing about this cage was the sata power cable were sorta peeking around the fan, so you could see where they were.

Oh well, 10 bucks to ship the cage back to Newegg for an RMA, hopefully the new one will arrive before the new drives come in, but if not, I got that covered. :p

Also, pictures.

Side panel with drive cage after redoing the cabling:
[ATTACH=CONFIG]244534[/ATTACH]

Other side panel with drive cage:
[ATTACH=CONFIG]244533[/ATTACH]

Front:
[ATTACH=CONFIG]244535[/ATTACH]

Drives arranged without drive cage (they all fit!).
[ATTACH=CONFIG]244536[/ATTACH]

EDIT: I'm quite tempted to just put the OS drive in the hot swap bay and leave the RAID drives inside. I know that kinda defeats the purpose of a hot swap bay... but still...

EDIT2: It looks like the array is out 2 disks - one is rebuilding and the other is sitting at "unconfigured (bad)" That doesn't sound good at all...

EDIT3: I fixed the unconfigured (bad) drive by making it as good and then readding it to the array. I followed the instructions here:
[http://erikimh.com/raid-rebuilding-foreign-disk-by-hand/](http://erikimh.com/raid-rebuilding-foreign-disk-by-hand/)

---

### Post by rubylaser on 2013-07-08
> **CharlesA said:**
> 
EDIT2: It looks like the array is out 2 disks - one is rebuilding and the other is sitting at "unconfigured (bad)" That doesn't sound good at all...

EDIT3: I fixed the unconfigured (bad) drive by making it as good and then readding it to the array. I followed the instructions here:
[http://erikimh.com/raid-rebuilding-foreign-disk-by-hand/](http://erikimh.com/raid-rebuilding-foreign-disk-by-hand/)

That's a nice looking setup.  Believe me, once you get a working hot swap setup, you will enjoy having your disks in there :)  Glad you figured out the unconfigured (bad) drive, I was going to provide directions but you figured it out before I had a chance :)

---

### Post by CharlesA on 2013-07-08
> **rubylaser said:**
> That's a nice looking setup.  Believe me, once you get a working hot swap setup, you will enjoy having your disks in there :)  Glad you figured out the unconfigured (bad) drive, I was going to provide directions but you figured it out before I had a chance :)

Thanks. It was nice while it lasted. Gogo gadget google. ;)

---

