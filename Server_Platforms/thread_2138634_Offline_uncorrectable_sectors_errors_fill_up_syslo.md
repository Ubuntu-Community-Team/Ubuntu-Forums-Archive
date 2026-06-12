---
title: "Offline uncorrectable sectors errors fill up syslog and kern.log no rellocation"
date: 2013-04-24
forum: Server Platforms
---

### Post by alecz20 on 2013-04-24
I have smard monitoring, and everyday it sends me an email saying that I have 8  Offline uncorrectable sectors and that I should look in syslog.

Syslog is spammed with this messages:
```

Apr 24 15:03:37 server kernel: [860011.240057] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr 24 15:03:37 server kernel: [860011.243238] ata1.00: BMDMA stat 0x65
Apr 24 15:03:37 server kernel: [860011.246409] ata1.00: failed command: READ DMA
Apr 24 15:03:37 server kernel: [860011.249561] ata1.00: cmd c8/00:08:39:e0:24/00:00:00:00:00/e0 tag 0 dma 4096 in
Apr 24 15:03:37 server kernel: [860011.249564]          res 51/40:05:3c:e0:24/00:00:00:00:00/e0 Emask 0x9 (media error)
Apr 24 15:03:37 server kernel: [860011.255909] ata1.00: status: { DRDY ERR }
Apr 24 15:03:37 server kernel: [860011.259088] ata1.00: error: { UNC }
Apr 24 15:03:37 server kernel: [860011.440040] ata1.00: configured for UDMA/100
Apr 24 15:03:37 server kernel: [860011.540040] ata1.01: configured for UDMA/100
Apr 24 15:03:37 server kernel: [860011.540053] ata1: EH complete

```

This message bloc repeats every second.

I know that I have bad blocks, and that the drive is failing, but I don't really care at this point. I just want it to stop spamming the logs.

I would also like to relocate the sectors

I used this article:
[http://www.gra2.com/article.php/20041015232512624](http://www.gra2.com/article.php/20041015232512624)

But it does not produce the expected result.

The same syslog has this line:
end_request: I/O error, dev sda, sector 2416700

Smartctl says the sector is 2416697

The drive passes the tests without problems but:
```

 5 Reallocated_Sector_Ct   0x0033   099   099   009    Pre-fail  Always       -       18
...
198 Offline_Uncorrectable   0x0031   100   100   009    Pre-fail  Offline      -       8

```

I follow the article and I dd the sector, but it does not get relocated


The filesystem is ext4 and the partioning is like this
```

Disk /dev/sda: 20.1 GB, 20060135424 bytes
255 heads, 63 sectors/track, 2438 cylinders, total 39179952 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x38ef9d17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     1959929      979933+  83  Linux
/dev/sda2         1959930    39166469    18603270    5  Extended
/dev/sda5         1959993     3919859      979933+  83  Linux
/dev/sda6        38186568    39166469      489951   82  Linux swap / Solaris
/dev/sda7         3919923    38186504    17133291   83  Linux

```

So the sector is on sda5
The block is 4096

This gives a FileSystem Block = 57088
b = (int)((L-S)*512/B)
int(2416700 - 1959993) * 512/4096 = 57088

then debugfs gives this:
```

root@server:/var/log# debugfs
debugfs 1.42 (29-Nov-2011)
debugfs:  open /dev/sda5
debugfs:  icheck 57088
Block   Inode number
57088   480
debugfs:  ncheck 480
Inode   Pathname
480     /lib/apt-xapian-index/cataloged_times.p

```

However that file does not exist.

Regardless, I zero the sectors from 57085 to 57095

But no help.

Am I doing something wrong?

How can I force relocation without doing a complete format of the partition?

---

### Post by matt_symes on 2013-04-24
Hi

You can only force reallocations - or reallocations can only happen - if you have areas to reallocate them to. 

> Offline uncorrectable sectors.

Sounds to me they they can't be reallocated as there is nowhere to reallocate them to.

Backup your data !!!

Please post your full SMART report so we can take a better look and not have to guess for you.

Kind regards

---

### Post by alecz20 on 2013-04-25
Thanks a lot for the reply.

Here is the output of **smartctl -a /dev/sda**

```

# smartctl -a /dev/sda
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-30-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG SV2001H
Serial Number:    11111111111111
Firmware Version: QN100-12
User Capacity:    20,060,135,424 bytes [20.0 GB]
Sector Size:      512 bytes logical/physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 1
Local Time is:    Thu Apr 25 08:40:01 2013 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x92) Offline data collection activity
                                        is in a Reserved state.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (  780) seconds.
Offline data collection
capabilities:                    (0x1b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        No Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        No General Purpose Logging support.
Short self-test routine
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        (   4) minutes.

SMART Attributes Data Structure revision number: 9
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000a   100   100   000    Old_age   Always       -       110
  4 Start_Stop_Count        0x0032   092   092   000    Old_age   Always       -       9022
  5 Reallocated_Sector_Ct   0x0033   099   099   009    Pre-fail  Always       -       18
  7 Seek_Error_Rate         0x000b   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0024   091   086   000    Old_age   Offline      -       9530
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       4513665
 12 Power_Cycle_Count       0x0032   097   097   000    Old_age   Always       -       3594
194 Temperature_Celsius     0x0022   163   118   000    Old_age   Always       -       25
197 Current_Pending_Sector  0x0033   253   253   009    Pre-fail  Always       -       0
198 Offline_Uncorrectable   0x0031   100   100   009    Pre-fail  Offline      -       8
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000b   100   100   051    Pre-fail  Always       -       18
201 Soft_Read_Error_Rate    0x000b   100   100   051    Pre-fail  Always       -       19

SMART Error Log Version: 1
Warning: ATA error count 0 inconsistent with error log pointer 2

ATA Error Count: 0
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

Error 0 occurred at disk power-on lifetime: 37613 hours (1567 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 88 08 39 e0 24 e0   8 sectors at LBA = 0x0024e039 = 2416697

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 39 e0 24 e0 00      08:20:30.000  READ DMA
  f8 00 00 00 00 00 e0 00      08:20:30.000  READ NATIVE MAX ADDRESS
  ec 00 00 00 00 00 a0 02      08:20:30.000  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      08:20:30.000  SET FEATURES [Set transfer mode]
  f8 00 00 00 00 00 e0 00      08:20:30.000  READ NATIVE MAX ADDRESS

Error -1 occurred at disk power-on lifetime: 37613 hours (1567 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 88 08 39 e0 24 e0   8 sectors at LBA = 0x0024e039 = 2416697

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 39 e0 24 e0 00      08:20:29.000  READ DMA
  f8 00 00 00 00 00 e0 00      08:20:29.000  READ NATIVE MAX ADDRESS
  ec 00 00 00 00 00 a0 02      08:20:29.000  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      08:20:29.000  SET FEATURES [Set transfer mode]
  f8 00 00 00 00 00 e0 00      08:20:29.000  READ NATIVE MAX ADDRESS

Error -2 occurred at disk power-on lifetime: 37613 hours (1567 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 88 08 39 e0 24 e0   8 sectors at LBA = 0x0024e039 = 2416697

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 39 e0 24 e0 00      08:20:28.000  READ DMA
  f8 00 00 00 00 00 e0 00      08:20:28.000  READ NATIVE MAX ADDRESS
  ec 00 00 00 00 00 a0 02      08:20:28.000  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      08:20:28.000  SET FEATURES [Set transfer mode]
  f8 00 00 00 00 00 e0 00      08:20:28.000  READ NATIVE MAX ADDRESS

Error -3 occurred at disk power-on lifetime: 37613 hours (1567 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 88 08 39 e0 24 e0   8 sectors at LBA = 0x0024e039 = 2416697

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 39 e0 24 e0 00      08:20:27.000  READ DMA
  f8 00 00 00 00 00 e0 00      08:20:27.000  READ NATIVE MAX ADDRESS
  ec 00 00 00 00 00 a0 02      08:20:27.000  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      08:20:27.000  SET FEATURES [Set transfer mode]
  f8 00 00 00 00 00 e0 00      08:20:27.000  READ NATIVE MAX ADDRESS

Error -4 occurred at disk power-on lifetime: 37613 hours (1567 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 88 08 39 e0 24 e0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  b0 d5 01 01 4f c2 00 00      08:20:31.000  SMART READ LOG
  f8 00 00 00 00 00 e0 00      08:20:31.000  READ NATIVE MAX ADDRESS
  ec 00 00 00 00 00 a0 02      08:20:31.000  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      08:20:31.000  SET FEATURES [Set transfer mode]
  f8 00 00 00 00 00 e0 00      08:20:31.000  READ NATIVE MAX ADDRESS

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     37604         -
# 2  Extended offline    Completed without error       00%     26581         -

Device does not support Selective Self Tests/Logging

```

As you can see there are   18 Reallocated Sectors and 8 Offline Uncorrectable sectors

There is also this:
```

  40 88 08 39 e0 24 e0   8 sectors at LBA = 0x0024e039 = 2416697

```
Which indicates sector 2416697 that I previously tried to fix

Finally, the drive passes the tests.

I am not sure exactly what the problem is with this drive.


The other thing I should mention is that the system load is very high, and top shows ovet 95% wa
I digged around and found that this:

```

 TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN     IO>    COMMAND
  942 be/3 root        0.00 B/s    0.00 B/s  0.00 % 99.99 % [jbd2/sda5-8]

```

Which confirms that the problem is in that partition.

Any insight is appreciated

---

### Post by tgalati4 on 2013-04-25
High IO waits means that the kernel requested some data from the drive and the drive took forever to provide it.  The  kernel is content to wait for a long time until that data is fetched.  Your drive is having some issues that may be beyond what SMART can measure.  SMART only captures two thirds of the common failure modes.  The other 1/3 happen but are not captured.  So even though you have a few bad sectors, there may be other issues that are causing issues.  If you want to salvage the drive, wipe it and attempt a low-level format using Samsung's utility--if they have one.

Even after that, the drive may not be fully functional.

The way to stop the syslog messages is to replace the drive or to remove SMART monitoring.

---

### Post by matt_symes on 2013-04-25
Hi

As an addendum to the previous post, jdb2 is ext3/4 journalling daemon. 

It's quite possible that it is having trouble updating the journal.

It may be attempting to update/check the journal and cannot read the information required to do so. That file you referenced on the drive that does not exist may be the cause of this.

The "uncorrectable sector count" may suggest damage on the platters or, as stated by the last poster, other electro-mechanical failure.

 A low level format is a good idea. The software to do this will only, i suspect, run under Windows, if it exists at all. 

You could also try to dd the entire drive but i would not expect success with this as you already cannot dd the damaged sectors.

Backup and get yourself a new drive :)

Kind regards

---

### Post by alecz20 on 2013-04-25
Thanks for the suggestions.

This drive is not critical for me, it is only the OS on it, and the whole computer is scheduled for decommissioning soon.

What I need to do now, is to prevent the log files from taking up the whole /var partition.

I tried disabling SMART on the drive using this command:

```

smartctl --smart=off /dev/sda

```

I also removed all tests from /etc/smartd.conf

However the errors still show up in the logs.
I even stopped the smart daemon. I think I'm not disabling the correct stuff.


Anything I am missing on this, or should I just run this everyday:

```

echo "" > /var/log/syslog
echo "" > /var/log/kern.log

```

On a side note, syslog should should not allow spamming of the log files.

I think it should just say something like:

```

Previous message block repeated N times

```
But this is another topic

---

### Post by matt_symes on 2013-04-25
Hi

You can filter what syslog will log by using.. filters :)

You'll need to edit /etc/rsyslog.conf. I would consider a regex filter.

As you come across as pretty tech literate so I'll point you to the man page section.

```
man rsyslog.conf | less +/"FILTER CONDITIONS"
```

Kind regards

---

### Post by tgalati4 on 2013-04-25
Syslog and dmesg already have repeat message markers, however some errors (like disk read errors) are so serious that it is fruitless to filter them out.  Linux expects perfect hardware and when your hardware is not perfect, it will let you know.

If you really want to experiment, try running a live USB with persistance.  That way you are running completely in RAM with no hard disk access at all.

---

### Post by alecz20 on 2013-04-26
I added these lines in /etc/rsyslog.conf

```


# filter sda messages:
:msg, contains, "ata1" ~
:msg, contains, "res 51/40:05:3c:e0:24" ~
:msg, contains, "[sda]" ~
:msg, contains, "72 03 11 04" ~
:msg, contains, "00 24 e0 3c" ~
:msg, contains, "I/O error, dev sda, sector 2416700" ~
:msg, contains, "Descriptor sense data with sense descriptors (in hex):" ~

*.* /var/log/syslog
*.* /var/log/kern.log


```

Now the spamming has stopped.
The %wa is still high, but at least the partition won't fill up.

According to [http://www.rsyslog.com/doc/rsyslog_conf_filter.html](http://www.rsyslog.com/doc/rsyslog_conf_filter.html)
startswith is much faster than regex, but it seemed more difficult to use, so I ended up using "contains"

I am not sure how to use regex, and if it would be more efficient than contains


Thanks for the help!

---

### Post by matt_symes on 2013-04-26
Hi

> **alecz20 said:**
> I added these lines in /etc/rsyslog.conf

```


# filter sda messages:
:msg, contains, "ata1" ~
:msg, contains, "res 51/40:05:3c:e0:24" ~
:msg, contains, "[sda]" ~
:msg, contains, "72 03 11 04" ~
:msg, contains, "00 24 e0 3c" ~
:msg, contains, "I/O error, dev sda, sector 2416700" ~
:msg, contains, "Descriptor sense data with sense descriptors (in hex):" ~

*.* /var/log/syslog
*.* /var/log/kern.log


```

Now the spamming has stopped.
The %wa is still high, but at least the partition won't fill up.

According to [http://www.rsyslog.com/doc/rsyslog_conf_filter.html](http://www.rsyslog.com/doc/rsyslog_conf_filter.html)
startswith is much faster than regex, but it seemed more difficult to use, so I ended up using "contains"

I am not sure how to use regex, and if it would be more efficient than contains


Thanks for the help!

What you have done there is fine. 

If jdb2 is giving you problems, you could always disable/remove the journal.

It's up to you to weigh up the pros and cons of doing this though.

Kind regards

---

