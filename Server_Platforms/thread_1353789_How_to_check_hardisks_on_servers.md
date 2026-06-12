---
title: "How to check hardisks on servers?"
date: 2009-12-13
forum: Server Platforms
---

### Post by rado3105 on 2009-12-13
I have server running ubuntu, there are two disks there, one CompactFlash card as disk(system disk) and second one WD(S.M.A.R.T capable) as storage disk. Is any way to check sectors online on that CF card(it has no S.M.A.R.T ability). For WD I Installed smartmoontools and has to do it mannualy(is any way to do it automatically and show info when I logon server using ssh...?).
smartctl -a /dev/sdb1 showed this:
> SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       2
  3 Spin_Up_Time            0x0003   195   180   021    Pre-fail  Always       -       7233
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       275
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   082   082   000    Old_age   Always       -       13798
 10 Spin_Retry_Count        0x0012   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       275
192 Power-Off_Retract_Count 0x0032   199   199   000    Old_age   Always       -       794
193 Load_Cycle_Count        0x0032   187   187   000    Old_age   Always       -       41982
194 Temperature_Celsius     0x0022   119   088   000    Old_age   Always       -       33
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       81
200 Multi_Zone_Error_Rate   0x0008   200   198   000    Old_age   Offline      -       0
SMART Error Log Version: 1
ATA Error Count: 30 (device log contains only the most recent five errors)
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

Error 30 occurred at disk power-on lifetime: 4225 hours (176 days + 1 hours)
  When the command that caused the error occurred, the device was doing SMART Offline or Self-test.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 08 4f 00 f4 e0  Error: IDNF 8 sectors at LBA = 0x00f4004f = 15990863

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  35 03 08 4f 00 f4 10 00      03:32:27.647  WRITE DMA EXT
  35 03 08 4f 00 ec 10 00      03:32:27.641  WRITE DMA EXT
  35 03 08 4f 00 74 10 00      03:32:27.635  WRITE DMA EXT
  35 03 08 4f 00 6c 10 00      03:32:27.629  WRITE DMA EXT
  35 03 08 4f 00 68 10 00      03:32:27.623  WRITE DMA EXT

Error 29 occurred at disk power-on lifetime: 214 hours (8 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 f0 4f 31 37 e0  Error: UNC 240 sectors at LBA = 0x0037314f = 3617103

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 03 f0 4f 31 37 1e 00      18:49:37.839  READ DMA EXT
  25 03 10 3f 31 37 1e 00      18:49:37.823  READ DMA EXT
  25 03 f0 4f 30 37 1e 00      18:49:37.819  READ DMA EXT
  25 03 a0 af 2f 37 1e 00      18:49:37.817  READ DMA EXT
  25 03 68 47 2f 37 1e 00      18:49:37.803  READ DMA EXT

Error 28 occurred at disk power-on lifetime: 214 hours (8 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 f0 8f 3b 25 e0  Error: UNC 240 sectors at LBA = 0x00253b8f = 2440079
 Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 03 f0 8f 3b 25 1e 00      18:47:28.400  READ DMA EXT
  25 03 10 7f 3b 25 1e 00      18:47:28.394  READ DMA EXT
  25 03 f0 8f 3a 25 1e 00      18:47:28.391  READ DMA EXT
  25 03 10 7f 3a 25 1e 00      18:47:28.390  READ DMA EXT
  25 03 f0 8f 39 25 1e 00      18:47:28.387  READ DMA EXT

Error 27 occurred at disk power-on lifetime: 213 hours (8 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 df 6c 34 e0  Error: UNC 8 sectors at LBA = 0x00346cdf = 3435743

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 03 08 df 6c 34 18 00      18:04:12.607  READ DMA EXT
  25 03 08 87 4c 34 18 00      18:04:12.602  READ DMA EXT
  25 03 40 a7 2c 34 18 00      18:04:12.597  READ DMA EXT
  25 03 20 87 2c 34 18 00      18:04:12.585  READ DMA EXT
  25 03 28 5f 2c 34 18 00      18:04:12.583  READ DMA EXT

Error 26 occurred at disk power-on lifetime: 195 hours (8 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 4f 00 cc e0  Error: UNC 8 sectors at LBA = 0x00cc004f = 13369423

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 03 08 4f 00 cc 49 00      00:06:51.590  READ DMA EXT
  25 03 08 4f 00 04 43 00      00:06:51.578  READ DMA EXT
  25 03 08 4f 00 e0 3d 00      00:06:51.568  READ DMA EXT
  25 03 08 4f 00 5c 40 00      00:06:51.556  READ DMA EXT
  25 03 08 4f 00 68 3a 00      00:06:51.549  READ DMA EXT

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


It shows some errors can anybody explain if that this is going to fail?

---

### Post by Queue29 on 2009-12-13
Running a normal operating system (read: not optimized for limited reads/writes to disk) like Ubuntu is going to kill that flash card in a matter of months.

---

### Post by rado3105 on 2009-12-13
what do you recommend for that server as main hardisk, I just need something about 8G and parameters like CF?

---

### Post by garfonzo on 2009-12-13
> **rado3105 said:**
> what do you recommend for that server as main hardisk, I just need something about 8G and parameters like CF?

Why not a hard disk? I went to my local computer shop and they gave me 5 used hard drives for $10 each. Each one of them varied from 4GB-20GB each. Now I've got a bunch of hard drives perfect for the OS of any server. My main house server is running off of one of these 20GB units. 

If/when it dies I'll just pop in another one. The disks my data is stored on are all high quality disks.

Funny story - of those 5 disks I had purchased second hand, one of them hadn't been wiped clean. It contained a full Windows install complete with a ton of personal pictures/documents/music/videos of whoever owned the hard drive before me. Crazy!

---

### Post by Queue29 on 2009-12-14
What I do is use a cheap "green" 80gig HDD as the system disk, and a CF card to hold weekly(ish) backups of the content of my site.

A better solution would be to buy an external hdd and make full backups, but I'm too cheap for that. :KS

---

### Post by lavinog on 2009-12-14
> **Queue29 said:**
> Running a normal operating system (read: not optimized for limited reads/writes to disk) like Ubuntu is going to kill that flash card in a matter of months.

It is a server, not a desktop.

CF can be used to hold the os...That is how some wind PCs are designed.
I have been running a server off of a CF card for 2 years now.

Flash media is limited in writes to about 100,000 writes per sector.  Wear leveling extends the life also.  As long as the drive has a good amount of free space it should be fine.

If the home partition is stored on the hd, there shouldn't be a big problem.  The only thing that would be causing writes then would be the system logs, those should be pretty minor.  I have thought about using a ramdisk to hold the logs and sync them to the hd every hour...but the cost of a new CF is so cheap, I am not worried about it.

To the OP.
SMART is not the same as checking the drive for errors...CF doesn't use SMART because there are no moving parts.  SMART is not going to tell you if there is a filesystem error.  I have had many drives fail without giving a SMART warning.  The most important thing to have is a good backup solution.

For the record, it is possible that the CF will outlast the HD.

---

### Post by rado3105 on 2009-12-14
Thank you lavinog, it was very helpful. How you solved the backup? Is any way to check that drive using some script...?or..?

---

### Post by lavinog on 2009-12-14
you can force a file system check by using this command:
```

sudo touch /forcefsck

```
then reboot, it will check all mountable partitions for errors on next reboot.

I use rsync for backups.  It is very handy to learn how to use it.  Most backup programs are just frontends to rsync.
```

rsync -Pavux /home otherserver:/backups/home

```
P shows the progress
a is for archive (it is a couple of switches handy for backups)
v is for verbose (gives more detailed information)
u is for update
x is for same filesystem...don't backup things that don't exist on the filesystem (like gvfs mounts..etc)
The otherserver in this case is via a ssh connection.

---

### Post by Krupski on 2009-12-14
> **Queue29 said:**
> Running a normal operating system (read: not optimized for limited reads/writes to disk) like Ubuntu is going to kill that flash card in a matter of months.

Uh-oh... don't let *my* file server hear that. It's been running on a 4 GB UDMA compact flash card 24-7 for over a year.

The HARD DRIVES, on the other hand, haven't been completely reliable (thank goodness for RAID).

---

### Post by Krupski on 2009-12-14
> **rado3105 said:**
> what do you recommend for that server as main hardisk, I just need something about 8G and parameters like CF?

I recommend a compact flash card. I find 4 GB is more than enough for me... if you need 8G... go for it.

---

### Post by Krupski on 2009-12-14
> **rado3105 said:**
> what do you recommend for that server as main hardisk, I just need something about 8G and parameters like CF?

I also routinely backup my entire OS from the CF card using DCFLDD (a high powered version of DD).

Here's my little script called "savecf" that backs up the CF card:

```

#! /bin/bash
imagepath=/home/shared/linux/backups/
imagename=ubuntu-server-snapshot-$(date +%d-%b-%Y-%H%M).vhd
imagetime=$(date +%Y%m%d%H%M)
/bin/echo Saving OS image, please wait...
/usr/bin/dcfldd if=/dev/disk/by-id/edd-int13_dev80 of=$imagepath$imagename
/bin/touch -t$imagetime $imagepath$imagename
/bin/sync
/bin/echo "Done!"

```

...and here's what it saves...

```

-rw-r--r-- 1 root   root    4009549824 2009-12-14 21:31 ubuntu-server-snapshot-14-Dec-2009-2131.vhd

```

This way, if I make a boo-boo, I can just pop the CF card out of the server, copy a last-known-good image back to it (in Windows using Winimage) then pop the card back into the server and be back up and running in 5 minutes.

By the way, "/bin/dd" could be substituted for "/usr/bin/dcfldd" in the script and it would work equally as well (except it wouldn't show the backup progress like DCFLDD does).

-- Roger

---

### Post by lavinog on 2009-12-14
I will have to give DCFLDD a try, I have been using ddrescue lately in place of dd.

---

### Post by Krupski on 2009-12-15
> **lavinog said:**
> I will have to give DCFLDD a try, I have been using ddrescue lately in place of dd.

"dcfldd" and "dd" are basically the same thing. "dcfldd" just has more options.

In particular, it can display it's progress, which I prefer my script to do.

---

### Post by Xianath on 2009-12-17
Funny you should mention that. I just do [FONT="Courier New"]watch -n 1 'kill -USR1 `pidof dd`'[/FONT] in another console but I like this beefed up version of dd better. Thanks for the tip :)

Cheers,
Peter

---

### Post by Vegan on 2009-12-17
I have Linux Desktop on a USB stick and it works fine. I have let it run for a year on a notebook with no disk and it has run fine for 3 years now.

I use it to download stuff to a second stick when other machines are down.

---

