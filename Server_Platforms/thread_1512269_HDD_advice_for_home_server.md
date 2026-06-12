---
title: "HDD advice for home server?"
date: 2010-06-17
forum: Server Platforms
---

### Post by j-g-faustus on 2010-06-17
Hi,

I set up a home server about a year ago, it's primary purpose is to be up and running 24/7 and serve as backup, media storage and a few other odds and ends. It's currently running Ubuntu 10.04 LTS.

What has me concerned is the smartctl output I got today, it says that /dev/sda, the OS disk, has a start-stop count of 186,000 (!) and may be nearing failure (the smartctl value is 001 vs. the threshold of 000).

Divided on 7820 power-on hours, it means that the disk has been starting and stopping on average every 2.5 minutes for close to a year, which sounds slightly excessive for a computer I'm using at most a couple of times per day.

Do I have something wrong in my setup? 

Or could it be related to the OS disk being a 2.5" laptop disk? (The four other HDDs, 3.5" WD Green 1.5TB running in a RAID 5, seem entirely normal, no excessive values from smartctl.)

Any advice would be appreciated, whether on configuration changes or avoiding laptop disks in the future.

Here is my /etc/hdparm.conf:
---
/dev/sda {
  apm = 127
  spindown_time = 120
}
---

and the full output from smartctl:

---
/dev/sda:
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   160   159   021    Pre-fail  Always       -       958
  4 Start_Stop_Count        0x0032   001   001   000    Old_age   Always       -       185875
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   090   090   000    Old_age   Always       -       7820
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       109
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       39
193 Load_Cycle_Count        0x0032   118   118   000    Old_age   Always       -       246833
194 Temperature_Celsius     0x0022   107   098   000    Old_age   Always       -       36
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   100   253   051    Pre-fail  Offline      -       0
---

Regards,
jf

---

### Post by j-g-faustus on 2010-06-19
OK, I think I figured it out - it was a combination of aggressive APM settings and that laptop-mode had stopped working at some point during an earlier upgrade.

For anyone else with similar problems, there's some [more info here]("http://superuser.com/questions/153982/home-server-hard-drive-186k-start-stop-cycles-in-325-days").

---

