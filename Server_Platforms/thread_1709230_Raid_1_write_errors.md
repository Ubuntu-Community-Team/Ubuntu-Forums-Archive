---
title: "Raid 1 write errors"
date: 2011-03-17
forum: Server Platforms
---

### Post by wyldeone on 2011-03-17
I have an Ubuntu server set up with two SATA drives in a RAID 1 configuration with MDADM. The machine is used to record raw video, which involves a lot of writing to the disk. Sometimes during video recording the computer will crash, will the following errors in kern.log:

```

Mar 15 10:39:41 chapel-video kernel: [414501.629864] ata2.00: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x6
Mar 15 10:39:41 chapel-video kernel: [414501.629870] ata2.00: BMDMA stat 0x26
Mar 15 10:39:41 chapel-video kernel: [414501.629875] ata2.00: SError: { UnrecovData Handshk }
Mar 15 10:39:41 chapel-video kernel: [414501.629880] ata2.00: failed command: WRITE DMA EXT
Mar 15 10:39:41 chapel-video kernel: [414501.629889] ata2.00: cmd 35/00:00:28:6d:f6/00:04:06:00:00/e0 tag 0 dma 524288 out
Mar 15 10:39:41 chapel-video kernel: [414501.629891]          res 51/84:b1:77:6e:f6/84:02:06:00:00/e0 Emask 0x30 (host bus error)
Mar 15 10:39:41 chapel-video kernel: [414501.629896] ata2.00: status: { DRDY ERR }
Mar 15 10:39:41 chapel-video kernel: [414501.629899] ata2.00: error: { ICRC ABRT }
Mar 15 10:39:41 chapel-video kernel: [414501.629910] ata2.00: hard resetting link
Mar 15 10:39:41 chapel-video kernel: [414501.973009] ata2.01: hard resetting link
Mar 15 10:39:41 chapel-video kernel: [414502.482642] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Mar 15 10:39:41 chapel-video kernel: [414502.482658] ata2.01: SATA link down (SStatus 0 SControl 300)
Mar 15 10:39:41 chapel-video kernel: [414502.546160] ata2.00: configured for UDMA/133
Mar 15 10:39:41 chapel-video kernel: [414502.546203] ata2: EH complete
```

Is this the result of faulty drives? Is software RAID just not performant enough for data rates ~15 MB/s, even with a quad-core i7?

Thanks for your help.

---

### Post by rubylaser on 2011-03-17
mdadm can do far more than 15 MB/s without a problem.  This looks like either a bad SATA cable, SATA head, or a hard drive problem.  Have you tested the drives with SMART, and swapped cables.  Also, what do you have in your syslog?
```
cat /var/log/syslog | grep disk
```

---

### Post by tgalati4 on 2011-03-18
What's the make and model of the disk drive?  Typically, only enterprise-class (business-grade) drives can sustain continuous writing.  Consumer drives are not robust enough for continuous writing.  

Since writing takes more current, the heads heat up during continuous writes and misalignment or delamination can occur which causes errors.  Writing continuous video would definitely toast a consumer drive.

---

### Post by nathan58 on 2011-03-18
Maybe or not... Hi...for more solutions regard your problem you should consultant to your Linux Ubuntu administration.

---

### Post by wyldeone on 2011-03-20
> **rubylaser said:**
> mdadm can do far more than 15 MB/s without a problem.  This looks like either a bad SATA cable, SATA head, or a hard drive problem.  Have you tested the drives with SMART, and swapped cables.  Also, what do you have in your syslog?
```
cat /var/log/syslog | grep disk
```

```
Mar 17 11:46:44 chapel-video kernel: [    2.021699] PM: Resume from disk failed.
Mar 17 11:46:44 chapel-video kernel: [    2.719992] sd 1:0:0:0: [sdb] Attached SCSI disk
Mar 17 11:46:44 chapel-video kernel: [    2.720729] sd 0:0:1:0: [sda] Attached SCSI disk
Mar 17 11:46:44 chapel-video kernel: [    4.135085] sd 4:0:0:0: [sdc] Attached SCSI removable disk
Mar 17 12:32:21 chapel-video kernel: [    2.061504] PM: Resume from disk failed.
Mar 17 12:32:21 chapel-video kernel: [    2.756098] sd 1:0:0:0: [sdb] Attached SCSI disk
Mar 17 12:32:21 chapel-video kernel: [    2.767579] sd 0:0:1:0: [sda] Attached SCSI disk
Mar 17 12:32:21 chapel-video kernel: [    4.043522] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Mar 17 12:32:21 chapel-video kernel: [    4.173066] sd 4:0:0:0: [sdc] Attached SCSI removable disk
Mar 20 20:48:31 chapel-video kernel: [    2.061742] PM: Resume from disk failed.
Mar 20 20:48:31 chapel-video kernel: [    2.758525] sd 1:0:0:0: [sdb] Attached SCSI disk
Mar 20 20:48:31 chapel-video kernel: [    2.763339] sd 0:0:1:0: [sda] Attached SCSI disk
Mar 20 20:48:31 chapel-video kernel: [    3.924449] sd 4:0:0:0: [sdc] Attached SCSI removable disk
Mar 20 20:48:31 chapel-video kernel: [    4.041816] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
```

---

### Post by disabledaccount on 2011-03-21
You have damaged SATA cable or one of the HDD's what results in huge I/O delays, parcularily due to interface resetting. Show results of:
>smartctl -A /dev/sda (and sdb)

Besides, write performance depends on many factors.
You have connected both drives to the same physical channel - that cuts Your SATA interface troughoutput by more than halve. That can also lead to system crash, because it's more likely to lock both drives during interface resetting. (Switch one of the drives to another SATA port)
Best performance can be achieved by placing journal and write-intent-bitmap on separate array/drive, but this needs more HDD's. Cheaper solution is to switch journaling to write-back mode, and set noatime/relatime flag for filesystem - this dramatically reduces number of seeks.

edit: One more: still the most commonly made mistake is to use old style MBR partitions that are starting at LBA=63 - modern HDD will have lower overall performance in such case

---

### Post by wyldeone on 2011-03-21
For /dev/sda

```


=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   119   100   006    Pre-fail  Always       -       202688171
  3 Spin_Up_Time            0x0003   095   095   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       116
  5 Reallocated_Sector_Ct   0x0033   099   099   036    Pre-fail  Always       -       47
  7 Seek_Error_Rate         0x000f   063   060   030    Pre-fail  Always       -       1876952
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       255
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       58
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   099   099   000    Old_age   Always       -       36
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   058   051   045    Old_age   Always       -       42 (Lifetime Min/Max 42/42)
194 Temperature_Celsius     0x0022   042   049   000    Old_age   Always       -       42 (0 19 0 0)
195 Hardware_ECC_Recovered  0x001a   043   028   000    Old_age   Always       -       202688171
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       167104292585863
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       2432281820
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       3565093208
```

For /dev/sdb
```


=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   119   100   006    Pre-fail  Always       -       201762447
  3 Spin_Up_Time            0x0003   095   095   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       119
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   062   060   030    Pre-fail  Always       -       1638780
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       243
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       59
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   099   000    Old_age   Always       -       9
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   059   051   045    Old_age   Always       -       41 (Lifetime Min/Max 41/41)
194 Temperature_Celsius     0x0022   041   049   000    Old_age   Always       -       41 (0 17 0 0)
195 Hardware_ECC_Recovered  0x001a   032   029   000    Old_age   Always       -       201762447
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       3
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       259961485525361
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       2669561503
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       2009420827
```

---

### Post by disabledaccount on 2011-03-21
ehhh, Baracuda.
There is little chance that You can repair those drives (both) by upgrading the firmware - it depands on what model and what FW is currently installed (SDxx or CCxx)
Starting from Baracuda 11 Seagate makes more and more bugs in more and more buggy firmware - sad but true. The reason for failing raid are command timeouts: sda - 36 and sdb - 9. With these errors Your disk will be slow and get slower with time (or they just die)

Minor problems with SATA cable connected to sdb (UDMA CRC Error rate =3)

---

