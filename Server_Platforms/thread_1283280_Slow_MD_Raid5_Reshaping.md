---
title: "Slow MD Raid5 Reshaping"
date: 2009-10-05
forum: Server Platforms
---

### Post by gencha on 2009-10-05
I am currently in the process of growing a RAID5 from 3 to 5 disks. Sadly the reshaping process is excessively slow. It currently averages around 600K/sec but it occasionally goes up to values around 20000K/sec.
I have already increased /proc/sys/dev/raid/speed_limit_min but this only had an effect on the peaks not on the low average.
At this point I don't know what else I could try to determine the cause of this.

Also, is it possible to pause and resume the reshaping process so that I could reboot or check the hardware?

---

### Post by Xianath on 2009-10-06
Reshaping is indeed very slow. It's not hardware related at all, it's either a safety feature, or a bug. My array too resyncs at 90MB/sec but reshapes at 900k/sec. Try bumping up /sys/block/md*/md/sync_speed_min as well, though in my case that didn't work either.

Cheers,
Peter

---

### Post by gencha on 2009-10-07
It's already set to "30000 (system)". What I don't understand about the speed are the peaks where it runs a lot faster. I just find it hard to believe that it is "normal" for this process to take 2 weeks.

---

### Post by Xianath on 2009-10-08
What version of Ubuntu are you running? More specifically, what kernel and mdadm version? There were some bugs around sync_speed_min in older mdadm versions (2.8.6 was it?) Specifically, I think it affected 8.04.2 and earlier -- worth googling around as my memory is not what it used to be fifteen years ago.

Cheers,
Peter

---

### Post by gencha on 2009-10-08
If I remember correctly I installed 8.04.3 on this server.
```

# uname -a
Linux dump 2.6.24-24-server #1 SMP Tue Aug 18 16:51:43 UTC 2009 x86_64 GNU/Linux
# dpkg -l | grep mdadm
ii  mdadm                                 2.6.3+200709292116+4450e59-3ubuntu3.1 tool to administer Linux MD arrays (software

```

---

### Post by Xianath on 2009-10-08
Actually, my memory had indeed failed me because the bug was related to interrupted --grow, not rebuild speed.

About the only two things I can think of is to give your component devices enough readahead, and your md device a large enough stripe_cache_size:

```
sar -bdpqu -P ALL 60 1
sudo blockdev --setra 63356 /dev/sd?
echo 2048 | sudo tee /sys/block/dev/md?/md/stripe_cache_size
sar -bdpqu -P ALL 60 1
```

**_!!! Note that you need enough RAM to hold these buffers !!!_** Specifically:

32MB per component disk for read-ahead buffer
2048*chunk_size*nr_disks for stripe cache

Is there any significant difference in sar output before and after the change? Any noticeable change in resync speed?

Cheers,
Peter

---

### Post by gencha on 2009-10-08
After further searching the net on this matter I found a thread where someone reported similar problems and was advised to post iostat output.
When I run iostat I get this:
```

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.05    0.00    1.68    0.02    0.00   98.26

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda             513.81   355.67   48.03   86.17  4494.78  3539.44    59.86     0.70    5.25   0.56   7.49
sdb             513.59   356.00   48.26   85.84  4494.78  3539.44    59.91     0.76    5.64   0.56   7.51
sdc             511.62   355.06   50.22   86.78  4494.78  3539.44    58.64     0.61    4.48   0.52   7.18
sdd               0.00   351.09    0.00   90.75     0.00  3539.44    39.00     0.87    9.54  10.54  95.69
sde               0.00   355.59    0.00   86.25     0.00  3539.44    41.04     0.37    4.31   1.19  10.23
sdf               0.00     0.02    0.01    0.04     0.17     0.47    15.45     0.00   10.04   9.06   0.04
dm-0              0.00     0.00    0.01    0.06     0.16     0.47     9.52     0.00   27.03   6.22   0.04
dm-1              0.00     0.00    0.01    0.06     0.16     0.47     9.70     0.00   27.50   6.32   0.04
dm-2              0.00     0.00    0.00    0.00     0.00     0.00     8.00     0.00   12.78   6.19   0.00
md0               0.00     0.00    0.00    0.00     0.00     0.00     7.98     0.00    0.00   0.00   0.00
dm-3              0.00     0.00    0.00    0.00     0.00     0.00     7.97     0.00    1.27   1.27   0.00

```
Particularly interesting for me is the drive where it says 95% utilization. What should I make of this? sdd and sde are identical drives. Is it possibly defective?

---

### Post by Xianath on 2009-10-08
Without a data collection interval, iostat reports instantaneous values, which might be way off. Try this and post the second set of CPU and device stats):

```
iostat -cdmx 60 2
```

Cheers,
Peter

---

### Post by gencha on 2009-10-08
I was actually spectating it for a while through 'watch' and the values seemed rather constant. Nevertheless here's the output you requested:
```

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.01    0.00    0.51    0.02    0.00   99.46

Device:         rrqm/s   wrqm/s     r/s     w/s    rMB/s    wMB/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00   124.55    0.00   38.60     0.00     0.64    33.86     0.15    3.79   0.46   1.78
sdb               0.00   123.28    0.00   39.87     0.00     0.64    32.78     0.10    2.40   0.40   1.58
sdc               0.00   122.75    0.00   40.40     0.00     0.64    32.35     0.08    1.98   0.36   1.47
sdd               0.00   120.67    0.00   42.48     0.00     0.64    30.76     5.93  140.21  23.49  99.78
sde               0.00   121.62    0.00   41.53     0.00     0.64    31.47     0.20    4.91   0.91   3.80
sdf               0.00     0.02    0.00    0.05     0.00     0.00    10.67     0.00    6.67   6.67   0.03
dm-0              0.00     0.00    0.00    0.07     0.00     0.00     8.00     0.00    7.50   5.00   0.03
dm-1              0.00     0.00    0.00    0.07     0.00     0.00     8.00     0.00    7.50   5.00   0.03
dm-2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
md0               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
dm-3              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00

```

---

### Post by Xianath on 2009-10-08
OK an average service time of 140ms is WAY too high. It's the disk, the cable, or the controller. Check out S.M.A.R.T. logs with smartctl -a. You're looking for these attributes:

**001. Read Error Rate**
The number of times a read operation failed to complete. Non-zero values indicate that there is a problem with either the platters or heads, and the disk needs immediate attention.

**005. Reallocated Sectors Count**
The total number of weak sectors that have been successfully reallocated from their original position to a dedicated region on the platters to preserve their data

**196. Reallocation Event Count**
The total number of allocation attempts, also including unsuccessful ones
Values of Reallocation Event Count that are significantly higher than those of Reallocated Sectors Count are indicative of serious problems with specific regions of the platters, probably scratches due to mechanical shock, as well as possibly a damaged magnetic head.

Reallocating weak sectors aims to avoid bad sector creep, a phenomenon whereby a weak sector tends to affect those adjacent to it due to the amount of times the head tries to read it, which are more likely to be weak anyway. It has to be noted that successfully reallocated sectors are not reported bad, so traditional surface scanning is useless to detect them. This information is available through S.M.A.R.T. and is updated at runtime, not only while running a dedicated diagnostics utility, which is of great benefit to highly available systems where downtime is unacceptable.

**197. Current Pending Sector Count**
The number of sectors designated for reallocation that have not been successfully reallocated yet but have not been given up on, either
Read errors do not typically cause reallocation, while a successful read or write to a currently pending sector will take it out of that list. This approach significantly reduces the number of false positives in reallocated sectors by removing spurious ones, thus saving the limited reallocation space for those that really need it. On the other hand, this conservative approach makes detecting weak sectors somewhat more.

**010. Spin Retry Count**
The total number of unsuccessful attempts to reach working rotational speed, typically an indication of problems in the motor, transmission, or bearings

**198. Uncorrectable Sector Count**
The total number of sectors that showed an Uncorrectable Bit error

These must all be zero. If some of them aren't, compare them to the same attributes from your other (working) hard drives, on the off chance that it's a vendor- or model-specific inconsistency. If your drive is in warranty, request an RMA and cite the S.M.A.R.T. information -- it should be enough. In addition, check the following parameter:

**188. Command Timeout **
The total number of interface (ATA/SCSI) commands that have been rolled back because the device did not respond in time, typically an indication in the signaling components -- cables, connectors, as well as the bus itself

If you have any of these, replace the cable (obviously while you're NOT rebuilding the array). If you have no spare cable, swap swap it for another disk's cable and see if the other disk is affected. If it's still the same disk, swap SATA ports with another disk to see if it's the disk or port. If the SATA port is faulty, RMA the motherboard, otherwise RMA the disk.

Finally, is smartctl -a lists some errors from the S.M.A.R.T. logs, please post them here.

HTH,
Peter

---

### Post by gencha on 2009-10-08
This is the whole output of smartctl:
```

root@dump:/sys/block/md0/md# smartctl -a /dev/sdd
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD15EADS-00P8B0
Serial Number:    WD-WMAVU0169350
Firmware Version: 01.00A01
User Capacity:    1,500,301,910,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Oct  8 15:04:06 2009 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x80) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                 (34560) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   253   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   183   183   021    Pre-fail  Always       -       5850
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       8
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       182
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       7
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       5
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       10
194 Temperature_Celsius     0x0022   104   104   000    Old_age   Always       -       46
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

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

I also ran smartctl for /dev/sde and the output is pretty much the same with some slight variations here and there. What I noticed is that it takes rather long to produce the output for /dev/sdd in comparison with /dev/sde.

---

### Post by Xianath on 2009-10-08
OK so the disk is brand new and S.M.A.R.T. is clean as virgin snow. Your note about probe speed leads me to believe it could still be the cable or port, just not bad enough to trigger actual errors. You obviously can't replace it while the array is reshaping, and though it *should* survive a clean shutdown... if it were my data, I wouldn't do it.

Not sure what to suggest at this point. Could it be the drive is not initialized properly? Can you 'cat /sys/block/sdd/device/queue_*' ? It should say something like "31 simple" if NCQ is working properly. Check dmesg, too:

```
dmesg | egrep -i 'NCQ|ATA|sd'
```

That's more or less all I can think of right now. Hopefully there will be something in dmesg to help with this.

Cheers,
Peter

---

### Post by gencha on 2009-10-08
Yeah I kinda feel the same way about stopping the reshaping process. Especially since reading bug reports about not being able to resume aborted reshaping processes.

As you guessed 'cat /sys/block/sdd/device/queue_*' prints "31 simple".

For dmesg I got this:
```

[   34.279761] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[   37.494266] ata1: SATA max UDMA/133 abar m8192@0xfcf7a000 port 0xfcf7a100 irq 2301
[   37.494268] ata2: SATA max UDMA/133 abar m8192@0xfcf7a000 port 0xfcf7a180 irq 2301
[   37.494270] ata3: SATA max UDMA/133 abar m8192@0xfcf7a000 port 0xfcf7a200 irq 2301
[   37.494273] ata4: SATA max UDMA/133 abar m8192@0xfcf7a000 port 0xfcf7a280 irq 2301
[   37.494275] ata5: SATA max UDMA/133 abar m8192@0xfcf7a000 port 0xfcf7a300 irq 2301
[   37.494277] ata6: SATA max UDMA/133 abar m8192@0xfcf7a000 port 0xfcf7a380 irq 2301
[   38.182612] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   38.195339] ata1.00: ATA-7: SAMSUNG HD154UI, 1AG01118, max UDMA7
[   38.195341] ata1.00: 2930277168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   38.891553] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   38.904249] ata2.00: ATA-7: SAMSUNG HD154UI, 1AG01118, max UDMA7
[   38.904251] ata2.00: 2930277168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   39.600501] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   39.613198] ata3.00: ATA-7: SAMSUNG HD154UI, 1AG01118, max UDMA7
[   39.613200] ata3.00: 2930277168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   39.969953] ata4: SATA link down (SStatus 0 SControl 300)
[   40.658940] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   41.132026] ata5.00: ATA-8: WDC WD15EADS-00P8B0, 01.00A01, max UDMA/133
[   41.132028] ata5.00: 2930277168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   41.827203] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   42.301352] ata6.00: ATA-8: WDC WD15EADS-00P8B0, 01.00A01, max UDMA/133
[   42.301354] ata6.00: 2930277168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   42.307071] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD154UI  1AG0 PQ: 0 ANSI: 5
[   42.307163] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD154UI  1AG0 PQ: 0 ANSI: 5
[   42.307232] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD154UI  1AG0 PQ: 0 ANSI: 5
[   42.307310] scsi 4:0:0:0: Direct-Access     ATA      WDC WD15EADS-00P 01.0 PQ: 0 ANSI: 5
[   42.307375] scsi 5:0:0:0: Direct-Access     ATA      WDC WD15EADS-00P 01.0 PQ: 0 ANSI: 5
[   42.838520] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   42.838522] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   43.195560] ata7.00: ATA-7: SAMSUNG SP0802N, TK100-24, max UDMA/100
[   43.195575] ata7.01: ATAPI: HL-DT-ST DVDRAM GSA-H12N, UL01, max UDMA/66
[   43.415179] scsi 6:0:0:0: Direct-Access     ATA      SAMSUNG SP0802N  TK10 PQ: 0 ANSI: 5
[   43.425076] Driver 'sd' needs updating - please use bus_type methods
[   43.425167] sd 0:0:0:0: [sda] 2930277168 512-byte hardware sectors (1500302 MB)
[   43.425178] sd 0:0:0:0: [sda] Write Protect is off
[   43.425180] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   43.425197] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.425258] sd 0:0:0:0: [sda] 2930277168 512-byte hardware sectors (1500302 MB)
[   43.425266] sd 0:0:0:0: [sda] Write Protect is off
[   43.425268] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   43.425282] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.425284]  sda: unknown partition table
[   43.433374] sd 0:0:0:0: [sda] Attached SCSI disk
[   43.433448] sd 1:0:0:0: [sdb] 2930277168 512-byte hardware sectors (1500302 MB)
[   43.433460] sd 1:0:0:0: [sdb] Write Protect is off
[   43.433462] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   43.433477] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.433515] sd 1:0:0:0: [sdb] 2930277168 512-byte hardware sectors (1500302 MB)
[   43.433523] sd 1:0:0:0: [sdb] Write Protect is off
[   43.433525] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   43.433539] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.433542]  sdb:<4>Driver 'sr' needs updating - please use bus_type methods
[   43.437715] sd 1:0:0:0: [sdb] Attached SCSI disk
[   43.437767] sd 2:0:0:0: [sdc] 2930277168 512-byte hardware sectors (1500302 MB)
[   43.437778] sd 2:0:0:0: [sdc] Write Protect is off
[   43.437780] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   43.437795] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.437833] sd 2:0:0:0: [sdc] 2930277168 512-byte hardware sectors (1500302 MB)
[   43.437842] sd 2:0:0:0: [sdc] Write Protect is off
[   43.437844] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   43.437858] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.437860]  sdc: unknown partition table
[   43.441128] sd 2:0:0:0: [sdc] Attached SCSI disk
[   43.441163] sd 4:0:0:0: [sdd] 2930277168 512-byte hardware sectors (1500302 MB)
[   43.441171] sd 4:0:0:0: [sdd] Write Protect is off
[   43.441173] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[   43.441187] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.441214] sd 4:0:0:0: [sdd] 2930277168 512-byte hardware sectors (1500302 MB)
[   43.441222] sd 4:0:0:0: [sdd] Write Protect is off
[   43.441223] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[   43.441237] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.441239]  sdd: unknown partition table
[   43.450702] sd 4:0:0:0: [sdd] Attached SCSI disk
[   43.450739] sd 5:0:0:0: [sde] 2930277168 512-byte hardware sectors (1500302 MB)
[   43.450747] sd 5:0:0:0: [sde] Write Protect is off
[   43.450749] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
[   43.450763] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.450790] sd 5:0:0:0: [sde] 2930277168 512-byte hardware sectors (1500302 MB)
[   43.450798] sd 5:0:0:0: [sde] Write Protect is off
[   43.450800] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
[   43.450813] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.450816]  sde: unknown partition table
[   43.457958] sd 5:0:0:0: [sde] Attached SCSI disk
[   43.457992] sd 6:0:0:0: [sdf] 156368016 512-byte hardware sectors (80060 MB)
[   43.458000] sd 6:0:0:0: [sdf] Write Protect is off
[   43.458001] sd 6:0:0:0: [sdf] Mode Sense: 00 3a 00 00
[   43.458014] sd 6:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.458042] sd 6:0:0:0: [sdf] 156368016 512-byte hardware sectors (80060 MB)
[   43.458049] sd 6:0:0:0: [sdf] Write Protect is off
[   43.458051] sd 6:0:0:0: [sdf] Mode Sense: 00 3a 00 00
[   43.458064] sd 6:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.458066]  sdf: sdf1 sdf2 < sdf5 >
[   43.469681] sd 6:0:0:0: [sdf] Attached SCSI disk
[   43.472976] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   43.472996] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   43.473015] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   43.473032] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   43.473049] sd 5:0:0:0: Attached scsi generic sg4 type 0
[   43.473066] sd 6:0:0:0: Attached scsi generic sg5 type 0
[  160.519127] EXT3 FS on sdf1, internal journal
[  270.117589] md: bind<sdb>
[  270.117705] md: bind<sdc>
[  270.117819] md: bind<sda>
[  271.478743] raid5: device sda operational as raid disk 0
[  271.478746] raid5: device sdc operational as raid disk 2
[  271.478749] raid5: device sdb operational as raid disk 1
[  271.479756]  disk 0, o:1, dev:sda
[  271.479757]  disk 1, o:1, dev:sdb
[  271.479759]  disk 2, o:1, dev:sdc
[  378.161982] md: bind<sdd>
[  381.530092] md: bind<sde>
[  401.061928]  disk 0, o:1, dev:sda
[  401.061930]  disk 1, o:1, dev:sdb
[  401.061931]  disk 2, o:1, dev:sdc
[  401.061932]  disk 3, o:1, dev:sde
[  401.061943]  disk 0, o:1, dev:sda
[  401.061944]  disk 1, o:1, dev:sdb
[  401.061945]  disk 2, o:1, dev:sdc
[  401.061946]  disk 3, o:1, dev:sde
[  401.061947]  disk 4, o:1, dev:sdd

```

---

### Post by gencha on 2009-10-13
So early this morning the RAID finished reshaping.
So the first thing I did was testing how it performs now.
I started an FTP transfer to the server and ran iostat -cmdx 60 2 again. And this is what I got:
```

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.30    0.00   27.39    0.22    0.00   72.10

Device:         rrqm/s   wrqm/s     r/s     w/s    rMB/s    wMB/s avgrq-sz avgqu-sz   await  svctm  %util
sda              52.47   857.83   16.82  576.93     0.27     5.61    20.29     1.51    2.55   0.30  18.02
sdb              56.02   866.95   16.53  569.58     0.29     5.62    20.63     1.60    2.74   0.31  18.35
sdc              54.40   863.57   16.23  573.60     0.28     5.62    20.48     1.49    2.52   0.29  17.12
sdd              49.38   897.20   16.82  536.77     0.26     5.61    21.71     2.33    4.21   0.43  23.57
sde              49.95   905.22   16.73  530.13     0.26     5.61    22.01     2.45    4.48   0.43  23.48
sdf               0.00     0.08    0.05    0.27     0.00     0.00    10.11     0.00   12.63  12.11   0.38
dm-0              0.00     0.00    0.05    0.35     0.00     0.00     8.00     0.01   13.75   9.58   0.38
dm-1              0.00     0.00    0.05    0.28     0.00     0.00     8.00     0.00   14.50  10.00   0.33
dm-2              0.00     0.00    0.00    0.07     0.00     0.00     8.00     0.00   10.00   7.50   0.05
md0               0.00     0.00    0.17 5672.62     0.00    22.16     8.00     0.00    0.00   0.00   0.00
dm-3              0.00     0.00    0.17 5672.62     0.00    22.16     8.00   575.37  101.43   0.08  47.52

```
Now I am completely out of ideas. Now all drives are performing similarly well. So why was one drive performing so exceptionally bad during the reshaping process?
And is the next reshaping going to take a whole month?

---

### Post by gencha on 2009-10-13
Ok I have to revise that. After running more tests I am now back to this:
```

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.06    0.00    3.53   59.65    0.00   36.76

Device:         rrqm/s   wrqm/s     r/s     w/s    rMB/s    wMB/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.99    98.71    0.53   71.88     0.01     0.67    19.02     0.07    0.95   0.20   1.48
sdb               1.61    97.66    0.65   72.69     0.01     0.67    18.83     0.07    1.00   0.20   1.44
sdc               1.69    98.58    0.64   71.79     0.01     0.67    19.08     0.09    1.23   0.21   1.51
sdd               1.38   121.64    0.58   48.39     0.01     0.66    28.11    30.43  623.41  20.37  99.79
sde               1.79   103.22    0.74   66.84     0.01     0.66    20.43     0.13    1.92   0.25   1.70
sdf               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
dm-0              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
dm-1              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
dm-2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
md0               0.00     0.00    0.02  679.66     0.00     2.65     8.00     0.00    0.00   0.00   0.00
dm-3              0.00     0.00    0.02  691.42     0.00     2.70     8.00 102481911517081.97 148215428960295.84   1.44  99.81

```
I'll now start replacing items in the configuration.

---

### Post by gencha on 2009-10-13
Just FYI, I have now replace /dev/sdd with a new drive and am currently rebuild the array.
```

Personalities : [raid6] [raid5] [raid4]
md0 : active raid5 sde[5] sda[0] sdd[3] sdc[2] sdb[1]
      5860553984 blocks level 5, 64k chunk, algorithm 2 [5/4] [UUUU_]
      [>....................]  recovery =  3.6% (54177408/1465138496) finish=321.1min speed=73224K/sec

```
This looks promising so far.

Thanks for the help.

As a sidenote for people who might run into similar problems, before I added the new drive I had started the array without the faulty drive and tested write performance. And it was stable. I did not change the cable or controller port so I would change as little variables as possible in a single step.
To determine what physical device /dev/sdd actually was I used:
```

sudo smartctl -i /dev/sdd

```
This way I could later compare it determine if I disconnected the correct drive by comparing serial numbers.

---

