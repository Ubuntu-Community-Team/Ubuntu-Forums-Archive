---
title: "md raid 10 errors"
date: 2011-07-26
forum: Server Platforms
---

### Post by jjazz on 2011-07-26
Hi,

I've had this server for a while and I've periodically received similar errors, but it's been worse lately. I'm trying to diagnose and similar posts have left me with 2, maybe 3, ideas about what could be wrong. Here is the setup:
Ubuntu Server 10.10 maverick
kernel 2.6.35-30-server
Sans Digital TR8 8 bay raid - 2 port multipliers to esata outputs
8 1TB WD Caviar Black
Syba PCI-e card with Sil3124 chipset - 2 external esata inputs
I do not use the RocketRaid 622 card that came w/the enclosure because I had problems with drivers and configuration so I went with the SI chipset. The raid is configured with mdadm, level 10, running ext3 file system:
```

root@i5server:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid10 sdb1[5] sdg1[2] sdd1[7] sdh1[3] sdf1[1] sde1[0] sdc1[6] sda1[4]
      3906721792 blocks 256K chunks 2 far-copies [8/8] [UUUUUUUU]
      
unused devices: <none>

```

Error output:
```

Jul 26 17:53:28 i5server kernel: [81873.050364] ata1.00: failed to read SCR 1 (Emask=0x40)
Jul 26 17:53:28 i5server kernel: [81873.050372] ata1.01: failed to read SCR 1 (Emask=0x40)
Jul 26 17:53:28 i5server kernel: [81873.050376] ata1.02: failed to read SCR 1 (Emask=0x40)
Jul 26 17:53:28 i5server kernel: [81873.050380] ata1.03: failed to read SCR 1 (Emask=0x40)
Jul 26 17:53:28 i5server kernel: [81873.050384] ata1.04: failed to read SCR 1 (Emask=0x40)
Jul 26 17:53:28 i5server kernel: [81873.050387] ata1.05: failed to read SCR 1 (Emask=0x40)
Jul 26 17:53:28 i5server kernel: [81873.050396] ata1.15: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6 frozen
Jul 26 17:53:28 i5server kernel: [81873.051700] ata1.15: irq_stat 0x00060002, PMP DMA CS errata
Jul 26 17:53:28 i5server kernel: [81873.052979] ata1.00: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6 frozen
Jul 26 17:53:28 i5server kernel: [81873.054243] ata1.00: failed command: READ DMA EXT
Jul 26 17:53:28 i5server kernel: [81873.055605] ata1.00: cmd 25/00:00:00:08:59/00:02:05:00:00/e0 tag 1 dma 262144 in
Jul 26 17:53:28 i5server kernel: [81873.055606]          res 80/12:02:02:00:00/00:00:00:10:80/00 Emask 0x2 (HSM violation)
Jul 26 17:53:28 i5server kernel: [81873.058887] ata1.00: status: { Busy }
Jul 26 17:53:28 i5server kernel: [81873.060231] ata1.00: error: { IDNF }
Jul 26 17:53:28 i5server kernel: [81873.061551] ata1.01: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6 frozen
Jul 26 17:53:28 i5server kernel: [81873.063131] ata1.01: failed command: READ DMA EXT
Jul 26 17:53:28 i5server kernel: [81873.064518] ata1.01: cmd 25/00:00:00:08:59/00:02:05:00:00/e0 tag 2 dma 262144 in
Jul 26 17:53:28 i5server kernel: [81873.064518]          res 50/00:00:ff:09:59/00:00:05:00:00/e0 Emask 0x100 (unknown error)
Jul 26 17:53:28 i5server kernel: [81873.067274] ata1.01: status: { DRDY }
Jul 26 17:53:28 i5server kernel: [81873.068670] ata1.02: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6 frozen
Jul 26 17:53:28 i5server kernel: [81873.070096] ata1.02: irq_stat 0x00060002, device error via D2H FIS
Jul 26 17:53:28 i5server kernel: [81873.071517] ata1.02: failed command: READ DMA EXT
Jul 26 17:53:28 i5server kernel: [81873.072933] ata1.02: cmd 25/00:c0:62:83:58/00:02:05:00:00/e0 tag 0 dma 360448 in
Jul 26 17:53:28 i5server kernel: [81873.072933]          res 51/84:ef:62:83:58/00:01:05:00:00/e0 Emask 0x10 (ATA bus error)
Jul 26 17:53:28 i5server kernel: [81873.075840] ata1.02: status: { DRDY ERR }
Jul 26 17:53:28 i5server kernel: [81873.077292] ata1.02: error: { ICRC ABRT }
Jul 26 17:53:28 i5server kernel: [81873.078755] ata1.03: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6 frozen
Jul 26 17:53:28 i5server kernel: [81873.080294] ata1.04: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6 frozen
Jul 26 17:53:28 i5server kernel: [81873.081752] ata1.05: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6 frozen
Jul 26 17:53:28 i5server kernel: [81873.083212] ata1.15: hard resetting link
Jul 26 17:53:28 i5server kernel: [81873.083214] ata1: controller in dubious state, performing PORT_RST
Jul 26 17:53:30 i5server kernel: [81875.331143] ata1.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
Jul 26 17:53:30 i5server kernel: [81875.331722] ata1.00: hard resetting link
Jul 26 17:53:31 i5server kernel: [81875.690606] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
Jul 26 17:53:31 i5server kernel: [81875.690634] ata1.01: hard resetting link
Jul 26 17:53:31 i5server kernel: [81876.049524] ata1.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 26 17:53:31 i5server kernel: [81876.049549] ata1.02: hard resetting link
Jul 26 17:53:31 i5server kernel: [81876.398457] ata1.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 26 17:53:31 i5server kernel: [81876.398484] ata1.03: hard resetting link
Jul 26 17:53:32 i5server kernel: [81876.757329] ata1.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 26 17:53:32 i5server kernel: [81876.757356] ata1.04: hard resetting link
Jul 26 17:53:32 i5server kernel: [81877.106256] ata1.04: SATA link down (SStatus 0 SControl 320)
Jul 26 17:53:32 i5server kernel: [81877.106300] ata1.05: hard resetting link
Jul 26 17:53:32 i5server kernel: [81877.455178] ata1.05: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
Jul 26 17:53:32 i5server kernel: [81877.468434] ata1.00: configured for UDMA/100
Jul 26 17:53:32 i5server kernel: [81877.473332] ata1.01: configured for UDMA/100
Jul 26 17:53:32 i5server kernel: [81877.477577] ata1.02: configured for UDMA/100
Jul 26 17:53:32 i5server kernel: [81877.482421] ata1.03: configured for UDMA/100
Jul 26 17:53:32 i5server kernel: [81877.482518] ata1: EH complete
Jul 26 18:03:08 i5server kernel: [82450.904413] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jul 26 18:03:08 i5server kernel: [82450.907175] ata1.01: irq_stat 0x00060002, device error via D2H FIS
Jul 26 18:03:08 i5server kernel: [82450.910058] ata1.01: failed command: READ DMA EXT
Jul 26 18:03:08 i5server kernel: [82450.912311] ata1.01: cmd 25/00:00:00:8c:dc/00:04:0f:00:00/e0 tag 1 dma 524288 in
Jul 26 18:03:08 i5server kernel: [82450.912313]          res 51/84:ef:00:8c:dc/00:02:0f:00:00/e0 Emask 0x10 (ATA bus error)
Jul 26 18:03:08 i5server kernel: [82450.917754] ata1.01: status: { DRDY ERR }
Jul 26 18:03:08 i5server kernel: [82450.920519] ata1.01: error: { ICRC ABRT }
Jul 26 18:03:08 i5server kernel: [82450.923500] ata1.01: hard resetting link
Jul 26 18:03:08 i5server kernel: [82451.270609] ata1.01: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
Jul 26 18:03:08 i5server kernel: [82451.275441] ata1.01: configured for UDMA/100
Jul 26 18:03:08 i5server kernel: [82451.275512] ata1: EH complete

```

The 8 drives are sd[a-h] where a-d are on the first port multiplier and e-h are on the 2nd. For the sake of duplication I will only post difference of smartctl output as 99% is the same:

```

root@i5server:~# smartctl -A /dev/sda
smartctl 5.40 2010-03-16 r3077 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   180   176   021    Pre-fail  Always       -       3975
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       44
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   092   092   000    Old_age   Always       -       6073
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       39
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       33
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       10
194 Temperature_Celsius     0x0022   112   107   000    Old_age   Always       -       35
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       241
200 Multi_Zone_Error_Rate   0x0008   200   199   000    Old_age   Offline      -       88

root@i5server:~# smartctl -A /dev/sdb
...
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       3
...
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       245
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       16

root@i5server:~# smartctl -A /dev/sdc
...
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
...
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       2409
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

root@i5server:~# smartctl -A /dev/sdd
...
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       3
...
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       225
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       1

root@i5server:~# smartctl -A /dev/sde
...
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       1
...
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

root@i5server:~# smartctl -A /dev/sdf
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
...
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

root@i5server:~# smartctl -A /dev/sdg
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
...
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

root@i5server:~# smartctl -A /dev/sdh
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
...
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0


```

Based on what I've read/seen I'm supposing one of the following:
cable problem - I use shielded esata cables and I cleaned both the cables and the ports
port multiplier problem - since only drives a-d are showing errors in smartctl, this could also be related to the cable
disk problem - /dev/sdc has a high error count

What's odd is that the raid dropped out and completely locked up the computer multiple times, then marked one of the drives as failed. I did a readd on the drive and it rebuilt witout issue. Ran e2fsck -f to clean up the problems it had when it crashed, but as soon as I do heavy read/writes the errors start showing up again. This is primarily a media server for music and movies, but also for backups and printing. Heavy read/writes are generally transcoding movies and music which is what I was doing when it failed.

I'm hoping someone that has more in-depth knowledge can shed a bit more light on it. Any help is GREATLY appreciated.

---

### Post by psusi on 2011-07-26
Yes, it does look like some sort of hardware problem, likely either the cable or the multiplier.  Try swapping the two cables and see if the problem moves to the other drives.

---

### Post by ian dobson on 2011-07-27
Hi,

I would check the power to the drives on the port multiplier.

On my backend server I also have a port multiplier (jm393) and when I cut the power to any of the drives that are on the multiplier I see  "failed to read SCR " for all drives on the multiplier.

I don't know if you have a jm393 based port multiplier but it doesn't seem to support hot swap/linux complains for several seconds if you cut the power to one drive.

Regards
Ian Dobson

---

### Post by jjazz on 2011-07-27
Thanks for the info. I'm going to switch the cables later today. 

Would mdadm 'care' if I cross the cables in order to make sure it's not one of the ports on the sata card? Meaning sd[a-d] would become sd[e-h] and vice versa.

---

### Post by ian dobson on 2011-07-27
Hi,

I'm not quite sure how mdadm would react to you chaning the block device names (/dev/sdX). But the easiest solution would be:-

1) Edit your mdadm.conf with the new drive letters
2) update the initial-ramfs (used in early boot sequence and contains a copy of mdadm.conf)
3) Shutdown the box
4) Swap the cables as required
5) Boot and pray to tux.

Regards
Ian Dobson

---

### Post by psusi on 2011-07-27
mdadm.conf should not be specifying the exact devices to use as they can change designation every time you reboot.  Unless you manually specify them in mdadm.conf, mdadm will correctly handle it when they change names.  They also should not change names if you swap cables because the system does not know or care about cables.

---

### Post by bakegoodz on 2011-07-28
I'm not great at reading raw S.M.A.R.T data, but It does not look like SMART thinks there is a problem. I prefer just using pass/fail approach, which is kinda the idea behind SMART anyways. Use smartctl -H /dev/sdx
That being said even if SMART passes a drive, it still may have problems. Especially sector problems, which are being more common as drive densities go up. Modern drives remap these sectors pretty regularly, but I find that common desktop variety drives are slow and lazy with dealing with bad sectors which really upsets both software and hardware RAID, especially hardware RAID. The scam is that drive manufacturers will be happy to charge you more money with a drive that works much better with RAID. The RAID edition and enterprise series drives are just their top end consumer drives with better firmware that deals with bad sectors faster and better.

Enough of that. This is what I would do: I would plug one hard drive at a time into the motherboard, and run the drive manufacturers diagnostic boot disk and do a full scan on each drive. Either you will find a bad drive, or if not you will know your multiplier card is bad. Or it may find and repair bad sectors on a drive which would allow the RAID to rebuild successfully.

---

### Post by psusi on 2011-07-28
> **bakegoodz said:**
> but I find that common desktop variety drives are slow and lazy with dealing with bad sectors which really upsets both software and hardware RAID, especially hardware RAID.

It does not upset mdadm; only some stupid hardware raids that kick the drive out of the array if it doesn't respond quickly enough.  And it isn't a matter of being lazy; it is a matter of desktop drives keep retrying in the hope that eventually they might recover your data.  The "enterprise" drives have an option that the hardware raid cards can activate telling them to just give up fast so the raid can read from the other drive instead.

---

