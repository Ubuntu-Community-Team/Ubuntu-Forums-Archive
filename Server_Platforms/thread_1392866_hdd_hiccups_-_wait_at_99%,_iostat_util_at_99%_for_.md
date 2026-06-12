---
title: "hdd hiccups - wait at 99%, iostat util at 99% for NO reason?"
date: 2010-01-28
forum: Server Platforms
---

### Post by MavBlack on 2010-01-28
Hi guys,

I use this machine as a samba server with one small IDE hdd for system and one large SATA hdd (1.5TB) hooked via 4xSATA PCI card.  The machine has 1.5GB RAM, and is also to run 2 ktorrent clients inside two Xvncs.

The problem is, that even when ktorrent is doing nothing I observe A LOT of hdd activity to the point where movies or even mp3s stored on this server played via samba on a windows machine "stutter".  E.g. smplayer will repeat 5 second piece a few times before moving on to the next piece... and it goes on for a good 10 minutes, once it starts.
Even browsing directories is slow to the point where it takes 5-20 seconds to show the content in Total Commander (equivalent of Midnight Commander for windows).

I am not sure how I can track what is really happening.  Why would ktorrent clients create a massive I/O when there's virtually no traffic to/from them?  (I have total of 1kB/s down and 10kB/s up while taking the masurements below).

Or is there something wrong with the hdd? I had to send back the first one I got, it had plenty of bad sectors (this one does not though, as far as I can tell no data loss occured, just performance sucks).

Here's some diagnostic data, please let me know if there's anything else I should check.

```
root@server:/datapool/shared# iostat -x 10
Linux 2.6.31-3-generic (server)         10-01-28        _i686_  (1 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          14.00    0.00    1.40   84.80    0.00    0.00

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00     5.10    0.00    2.10     0.00    57.60    27.43     0.00    0.19   0.19   0.04
sda1              0.00     1.50    0.00    0.30     0.00    14.40    48.00     0.00    0.00   0.00   0.00
sda2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sda3              0.00     3.60    0.00    1.80     0.00    43.20    24.00     0.00    0.22   0.22   0.04
sdb               0.00     0.00    0.50    0.80   121.60     6.40    98.46     1.79 1786.46 764.31  99.36
sdb1              0.00     0.00    0.50    0.80   121.60     6.40    98.46     1.79 1786.46 764.31  99.36

``````
root@server:/datapool/shared# smartctl -a /dev/sdb
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD15EADS-00P8B0
Serial Number:    WD-WCAVU0090828
Firmware Version: 01.00A01
User Capacity:    1,500,301,910,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Jan 28 16:32:03 2010 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84) Offline data collection activity
                                        was suspended by an interrupting command from host.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                 (32760) seconds.
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
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   183   178   021    Pre-fail  Always       -       5833
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       25
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       1500
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       24
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       20
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       1506
194 Temperature_Celsius     0x0022   106   105   000    Old_age   Always       -       44
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

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
``````
root@server:/datapool/shared# uname -a
Linux server 2.6.31-3-generic #19-Ubuntu SMP Tue Jul 14 16:04:41 UTC 2009 i686 GNU/Linux

root@server:/datapool/shared# top
top - 16:51:28 up 7 days, 15:35,  1 user,  load average: 1.23, 1.69, 1.30
Tasks: 135 total,   1 running, 134 sleeping,   0 stopped,   0 zombie
Cpu(s): 17.2%us,  1.7%sy,  0.0%ni,  0.0%id, 80.8%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   1544156k total,  1184148k used,   360008k free,    46496k buffers
Swap:  2000084k total,    55636k used,  1944448k free,   220684k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 1936 self      18  -2  292m 139m  12m S 16.2  9.3 914:47.38 ktorrent
 1631 media     18  -2  852m 619m  14m D  1.0 41.1 995:57.40 ktorrent
 1654 self      18  -2 15796  10m 1664 S  0.7  0.7  65:19.32 Xvnc
17046 root      18  -2  2448 1196  912 R  0.7  0.1   0:00.04 top
 4168 mysql     20   0  141m 2564 1332 S  0.3  0.2   6:00.31 mysqld
25318 gadek     20   0 19108 4428 3640 D  0.3  0.3   0:18.69 smbd
    1 root      20   0  3084  552  496 S  0.0  0.0   0:02.05 init
... ... ...

root@server:/datapool/shared# lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 11)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 11)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G550 AGP (rev 01)
02:03.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
02:0a.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
02:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
02:0c.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value



```I already upgraded the memory (I was sure that was the problem), and I changed the network card, but it changed nothing.

Any comments and advice will be appreciated,

Gregory

---

### Post by wirelessmonkey on 2010-01-28
Run htop for a bit, and watch it closely.   

Your top output certainly shows ktorrent (media) sucking up a ton of memory.

---

### Post by MavBlack on 2010-01-29
I installed htop, but besides a more fancy output I don't see much more than with other tools. Is there something in particular I should be paying attention to?

Memory is not an issue, swap is almost unused and you see barely any activity on sda (swap hdd).


**Perhaps the question is:  HOW do I link the hdd activity to a particular program???**

---

### Post by wirelessmonkey on 2010-02-05
sorry for the late reply... iotop may be helpful to you, it is in the repositories, and will allow you to see what's taking up io.

---

### Post by Xianath on 2010-02-07
The WD1500EADS is a GreenPower-series disk. Most such disks (WD GP, Samsung EcoGreen etc.) have a tendency to spin down a lot, so you may want to start with trying to disable power saving and drive spindown (which, alas, may not be possible on the WD1500EADS). Looking at your perf stats though, your average wait time is 1.7 seconds and the average service time is 0.7 seconds -- this is HORRIBLE seek performance, close to that of a floppy disk (seriously!) and there's nothing wrong with the drive according to SMART.

I strongly suspect the PCI SATA adapter. First, it's PCI, meaning low bandwidth. Second, the Silicon Image 3114 is a SATA, not SATA2 controller and therefore lacks NCQ support. I realize this is an old box that doesn't have onboard SATA or PCIe but investing further into fixing it is probably pointless. Still, consider getting a SiI 3124-2 (note the -2) based card which supports SATA2 with NCQ. That, or you can probably get a used ICH7-based motherboard for the price of a new SATA2 controller.

HTH,
Peter

---

