---
title: "Is it true that SSDs fail withot warning ? How to know the health of my SSD ?"
date: 2020-01-26
forum: Ubuntu, Linux and OS Chat
---

### Post by linuxyogi on 2020-01-26
Is it true that SSDs fail withot warning ? How to know the health of my SSD ?

---

### Post by CatKiller on 2020-01-26
No. Less than hard drives do. A likely fail state for an SSD is that you can read data but no longer write data; the equivalent fail state for a hard drive is that you can't read or write data.

SSDs give SMART data like hard drives do, and NVMe drives have utilities that provide the same thing. Work has been done to get that NVMe stuff into the kernel so that you can access it with the standard interfaces, and that will be available in a future Ubuntu release.

---

### Post by oldfred on 2020-01-26
You can already get a lot of info on SSD (this from 20.04, have not checked if nvme command available to install. 
man nvme

```
fred@fred-Z170N-focal:~$ sudo nvme list
[sudo] password for fred: 
Node             SN                   Model                                    Namespace Usage                      Format           FW Rev  
---------------- -------------------- ---------------------------------------- --------- -------------------------- ---------------- --------
/dev/nvme0n1     S4P2NF0M514514L      Samsung SSD 970 EVO Plus 500GB           1         137.13  GB / 500.11  GB    512   B +  0 B   2B2QEXM7


```

```
fred@fred-Z170N-focal:~$ sudo nvme smart-log /dev/nvme0n1
Smart Log for NVME device:nvme0n1 namespace-id:ffffffff
critical_warning                    : 0
temperature                         : 52 C
available_spare                     : 100%
available_spare_threshold           : 10%
percentage_used                     : 0%
data_units_read                     : 59,462
data_units_written                  : 324,833
host_read_commands                  : 444,919
host_write_commands                 : 1,749,408
controller_busy_time                : 6
power_cycles                        : 4
power_on_hours                      : 15
unsafe_shutdowns                    : 2
media_errors                        : 0
num_err_log_entries                 : 0
Warning Temperature Time            : 0
Critical Composite Temperature Time : 0
Temperature Sensor 1                : 52 C
Temperature Sensor 2                : 55 C
Thermal Management T1 Trans Count   : 0
Thermal Management T2 Trans Count   : 0
Thermal Management T1 Total Time    : 0
Thermal Management T2 Total Time    : 0
fred@fred-Z170N-focal:~$ 



```

---

### Post by rbmorse on 2020-01-26
Outright failures are rare, but can happen.  I had an early production 1TB Western Digital Black nvme device die during the initial formatting.  Device was there, then it was not.  Nothing detected it.  My guess is the controller failed, but that's a guess.   

WD confirmed the device was dead and replaced it under warranty (c/s was excellent and fast), but I never found out exactly what happened.  Replacement has been running strong with no problems.

---

### Post by oldfred on 2020-01-26
Some life info:

hard drive life 
[https://www.backblaze.com/blog/hard-drive-stats-q2-2019/](https://www.backblaze.com/blog/hard-drive-stats-q2-2019/)
[https://www.backblaze.com/blog/backblaze-hard-drive-stats-q1-2019/](https://www.backblaze.com/blog/backblaze-hard-drive-stats-q1-2019/)

[http://hothardware.com/news/google-data-center-ssd-research-report-offers-surprising-results-slc-not-more-reliable-than-mlc-flash](http://hothardware.com/news/google-data-center-ssd-research-report-offers-surprising-results-slc-not-more-reliable-than-mlc-flash)
SSD life test 2015 final
[http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead](http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead)
SSD life test: 2014
[http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte](http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte)
[http://techreport.com/review/27062/the-ssd-endurance-experiment-only-two-remain-after-1-5pb](http://techreport.com/review/27062/the-ssd-endurance-experiment-only-two-remain-after-1-5pb)

---

### Post by saville on 2020-01-26
I started having flaky responses when using nautilus. Folders would not appear, for example. So I replaced the SSD and that fixed it.

---

### Post by TheFu on 2020-01-27
I've had SSDs fail slowly, giving lots of feedback and I've had one fail after about 2 yrs of use, no warning at all.  Both were "value" SSD brands - i.e. cheap.

I review SMART reports weekly for all my storage. Usually, there is some hint about issues and failures, but not always.  According to Backblaze reports, normal spinning disks fail without any clear SMART warning 22% of the time.

I've attended multiple storage training sessions by storage vendors and data recovery experts (the guy teaches Feds how to do data recovery). These were "introduction" sessions, not hands on and presentation-like, except the data recovery one. That was 2 hrs of actual data recovery using specialized hardware. Around 2017, storage vendors said it was safe to use enterprise SSDs in RAID0 for most business workloads after an initial break-in period of a few weeks. After that point, they were extremely reliable until the duration/endurance writes was up. Quality consumer SSDs are only slightly less reliable.  Personally, I've moved my virtual machines off RAID1 storage to a single, quality, SSD.  I can swap in a spinning disk and restore backups for each VM quickly, however.  Nothing replaces backups.

The Data recovery guy says he doesn't trust SSDs because there's nothing to be done and there's no way to ensure a data wipe actually wipes the data. If you want an SSD to be wiped, pull it apart and physically destroy each chip.

I'm currently using consumer SSDs from Samsung and Micron. Micron is the OEM for some brands you probably know and trust.  Both are about a year old. Don't just get the cheapest SSD even from the well-respected brands. The specific model matters.  Those with lower endurance specifications are made with cheaper chips. [https://www.howtogeek.com/444787/multi-layer-ssds-what-are-slc-mlc-tlc-qlc-and-mlc/](https://www.howtogeek.com/444787/multi-layer-ssds-what-are-slc-mlc-tlc-qlc-and-mlc/) explains the different sorts of SSDs.

For SSDs, watch *241 Total_LBAs_Written* to ensure it doesn't exceed the warranty number, along with all the other SMART data for normal disks.

---

### Post by linuxyogi on 2020-01-30
Thanks everyone for the replies.

> **TheFu said:**
> 
I review SMART reports weekly for all my storage. Usually, there is some  hint about issues and failures, but not always. 

Can you please teach me how to do that. I am using a sata SSD not a nvme drive.

```
$ inxi -D
Drives:    Local Storage: total: 111.79 GiB used: 36.30 GiB (32.5%) 
           ID-1: /dev/sda vendor: Samsung model: SSD 750 EVO 120GB size: 111.79 GiB 

```

---

### Post by CatKiller on 2020-01-30
> **linuxyogi said:**
> Can you please teach me how to do that. I am using a sata SSD not a nvme drive.

```
sudo apt install smartmontools
sudo smartctl -a /dev/sda
```

---

### Post by linuxyogi on 2020-01-30
> **CatKiller said:**
> ```
sudo apt install smartmontools
sudo smartctl -a /dev/sda
```

Thanks CatKiller. Here is the output. Please have a look and tell me the condition of my SSD. Also tell me which part of the output tells us about the condition so that I can check that myself in future.

```
# smartctl -a /dev/sda
smartctl 6.6 2017-11-05 r4594 [x86_64-linux-4.19.0-6-amd64] (local build)
Copyright (C) 2002-17, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Samsung based SSDs
Device Model:     Samsung SSD 750 EVO 120GB
Serial Number:    S33MNB0H582786V
LU WWN Device Id: 5 002538 d40eadaf3
Firmware Version: MAT01B6Q
User Capacity:    120,034,123,776 bytes [120 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Form Factor:      2.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2, ATA8-ACS T13/1699-D revision 4c
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Thu Jan 30 19:53:22 2020 IST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (    0) seconds.
Offline data collection
capabilities:              (0x53) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    No Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  64) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       5982
 12 Power_Cycle_Count       0x0032   096   096   000    Old_age   Always       -       3180
177 Wear_Leveling_Count     0x0013   094   094   000    Pre-fail  Always       -       26
179 Used_Rsvd_Blk_Cnt_Tot   0x0013   100   100   010    Pre-fail  Always       -       0
181 Program_Fail_Cnt_Total  0x0032   100   100   010    Old_age   Always       -       0
182 Erase_Fail_Count_Total  0x0032   100   100   010    Old_age   Always       -       0
183 Runtime_Bad_Block       0x0013   100   099   010    Pre-fail  Always       -       0
187 Uncorrectable_Error_Cnt 0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0032   075   048   000    Old_age   Always       -       25
195 ECC_Error_Rate          0x001a   200   200   000    Old_age   Always       -       0
199 CRC_Error_Count         0x003e   100   100   000    Old_age   Always       -       0
235 POR_Recovery_Count      0x0012   099   099   000    Old_age   Always       -       189
241 Total_LBAs_Written      0x0032   099   099   000    Old_age   Always       -       7465682615

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      5042         -
# 2  Short offline       Completed without error       00%      5041         -
# 3  Short offline       Completed without error       00%      5033         -
# 4  Short offline       Completed without error       00%      5032         -
# 5  Short offline       Completed without error       00%      5026         -
# 6  Short offline       Completed without error       00%      5025         -
# 7  Short offline       Completed without error       00%      5024         -
# 8  Short offline       Completed without error       00%      5018         -
# 9  Short offline       Completed without error       00%      5018         -
#10  Short offline       Completed without error       00%      5017         -
#11  Short offline       Completed without error       00%      5013         -
#12  Short offline       Completed without error       00%      5011         -
#13  Short offline       Completed without error       00%      5010         -
#14  Short offline       Completed without error       00%      5009         -
#15  Short offline       Completed without error       00%      5008         -
#16  Extended offline    Aborted by host               30%      5007         -
#17  Short offline       Completed without error       00%      5002         -
#18  Short offline       Completed without error       00%      5000         -
#19  Short offline       Completed without error       00%      4999         -
#20  Short offline       Completed without error       00%      4998         -
#21  Short offline       Completed without error       00%      4995         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
  255        0    65535  Read_scanning was never started
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

---

### Post by TheFu on 2020-01-30
There are 50+ threads here about using SMART data.  Have you reviewed any of those?

You need to run a long test once in a while.  There are 2 steps to using SMART.
1) run a test
2) review the output

Any values not understood can be googled for a better explanation than we will create here off the top of our heads.  Any number that is not 0 or not 100% should be researched. Anything with error in the name should be researched.

---

### Post by linuxyogi on 2020-01-30
> **TheFu said:**
> There are 50+ threads here about using SMART data.  Have you reviewed any of those?

You need to run a long test once in a while.  There are 2 steps to using SMART.
1) run a test
2) review the output

Any values not understood can be googled for a better explanation than we will create here off the top of our heads.  Any number that is not 0 or not 100% should be researched. Anything with error in the name should be researched.

This is the first time I am doing this. I will do what you said. In the meantime can you please have a look at my smartctl output and give me an approx idea?

---

### Post by linuxyogi on 2020-01-30
```
# smartctl -H /dev/sda
smartctl 6.6 2017-11-05 r4594 [x86_64-linux-4.19.0-6-amd64] (local build)
Copyright (C) 2002-17, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

```

smartctl -H /dev/sda tells directly about the SSD health.

Thanks to all.

---

### Post by TheFu on 2020-01-30
> **linuxyogi said:**
> ```
 
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

```

smartctl -H /dev/sda tells directly about the SSD health.

Thanks to all.

That is only the summary.  By the time it says FAILED, it is too late.  

The most useful way to use SMART data is to watch the changes for each parameter over time.  With SSDs, there's the endurance number which needs to be watched carefully and compared to the endurance design number from the manufacturer's specs.  The many threads here about SSD reliability should cover that, somewhere.

---

### Post by Skaperen on 2020-02-01
maybe it can be useful to get the data every hour and see what changes.  i'm going to start doing that today for my 3 devices.  i don't know if i should record -a output or -x output.  but i like the temp graph i get from -x.

---

### Post by kurt18947 on 2020-02-01
> **oldfred said:**
> You can already get a lot of info on SSD (this from 20.04, have not checked if nvme command available to install. 
man nvme

```
fred@fred-Z170N-focal:~$ sudo nvme list
[sudo] password for fred: 
Node             SN                   Model                                    Namespace Usage                      Format           FW Rev  
---------------- -------------------- ---------------------------------------- --------- -------------------------- ---------------- --------
/dev/nvme0n1     S4P2NF0M514514L      Samsung SSD 970 EVO Plus 500GB           1         137.13  GB / 500.11  GB    512   B +  0 B   2B2QEXM7


```

```
fred@fred-Z170N-focal:~$ sudo nvme smart-log /dev/nvme0n1
Smart Log for NVME device:nvme0n1 namespace-id:ffffffff
critical_warning                    : 0
temperature                         : 52 C
available_spare                     : 100%
available_spare_threshold           : 10%
percentage_used                     : 0%
data_units_read                     : 59,462
data_units_written                  : 324,833
host_read_commands                  : 444,919
host_write_commands                 : 1,749,408
controller_busy_time                : 6
power_cycles                        : 4
power_on_hours                      : 15
unsafe_shutdowns                    : 2
media_errors                        : 0
num_err_log_entries                 : 0
Warning Temperature Time            : 0
Critical Composite Temperature Time : 0
Temperature Sensor 1                : 52 C
Temperature Sensor 2                : 55 C
Thermal Management T1 Trans Count   : 0
Thermal Management T2 Trans Count   : 0
Thermal Management T1 Total Time    : 0
Thermal Management T2 Total Time    : 0
fred@fred-Z170N-focal:~$ 



```

I have an HP 920 NvME M2 SSD. I'm using Ubuntu 18.02 with the HWE kernel & updated Xorg. My SSD is not recognized by either gnome-disks or GSmartControl. They know there's a disk there, they just don't know which one so don't produce any info. Perhaps that will change with 20.04.

---

### Post by oldfred on 2020-02-01
In 20.04 Disks shows my SSD, but the smart status in Disks is not active.

---

### Post by g3kxyz on 2020-02-04
I tried nvme on a ubuntu 18.04 machine but it didn't list my SSD.

---

