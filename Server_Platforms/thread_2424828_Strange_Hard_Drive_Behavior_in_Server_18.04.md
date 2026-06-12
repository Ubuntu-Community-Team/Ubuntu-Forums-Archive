---
title: "Strange Hard Drive Behavior in Server 18.04"
date: 2019-08-15
forum: Server Platforms
---

### Post by papkee on 2019-08-15
Hi All!

I've got a very basic Server 18.04 setup running that acts as my NAS/webserver/etc. Recently I picked up two HGST 1TB drives to add another Raid 1 array to the machine. The drives are 5400RPM 8MB cache, so nothing spectacular, but they were cheap. I noticed when building the array, mdadm was resycing at just over 1MB/s and it was going to take something like three days to finish. So obviously something was up. I suspected bad drives and began some testing to find out what was going on.

First some basic read tests, **hdparm -Tt /dev/sd<x>** showed both drives reading at around 40MB/s. Not spectacular by any means. The much more interesting test was write speeds. Moving on to a write test using **dd of=/dev/zero if=/dev/sd<x> bs=8k count=<y>**, I saw interesting behavior. If I limited the count to under 1000 (meaning under 8MB of data written - the drive's cache size) I was getting great speeds, up to around 100MB/s. As soon as I went over 1000, though, write speeds plummeted to anywhere from 1MB/s, to 6MB/s if I was lucky.

So obviously at this point I'm thinking it's bad hard drives. Just to make sure it wasn't a drive bay issue, I swapped a known good drive (but still an older, slower one) into the same bay and got much more reasonable results - 80MB/s read from hdparm and 50MB/s from the dd.

Just because these were new-ish drives (manufacturer refurb units but still...) I wanted to double check my results. I hooked up one of them to my windows machine via a USB-Sata adapter and ran CrystalDiskMark. It showed pretty much normal speeds for a USB2 adapter - 100MB/s read and 50MB/s write. The other drive was also just as fine.

So here's the question: what in the world would be causing these drives to behave fine in windows but have terrible write speeds and mediocre read speeds in Ubuntu? The only thing I can think of is that the drives are labelled "advanced format" and I read that nearly a decade ago that was causing some issues with older Ubuntu releases. But as far as I can tell that shouldn't be any sort of problem in the modern age.

All help and suggestions are appreciated. I'm still a relative novice as a server owner and linux user but this is the first time I've ever seen weird behavior like this.

---

### Post by TheFu on 2019-08-15
Check the SMART data.
Check that the partitions are aligned.

Any chance you've confused MBps and Mbps?  There is an 8x difference.  Disk and network performance is Mbps, almost always.
I've never seen over 22Mbps with USB2 disks in a RAID.

Did you tune the hdparms to optimal for the RAID sizes?

---

### Post by papkee on 2019-08-15
Sorry, I should probably clarify things a bit since that first post was a bit rambling. I'm doing testing on the individual drives here. I stopped the raid resync when it said it was going to take multiple days. The drives are now fully blank and I've only been creating simple partitions for the tests I've been running in Win10 and Ubuntu.

To answer your questions:

-SMART is 100% okay and looks like a nearly brand new drive for both.
-I'm doing testing on single partitions on the drives separately, as mentioned above they're not in an array yet.
-Yes, I know the difference between MB and Mb, and I'm referring to bytes here. That's the unit that hdparm, dd, and CrystalDisk all report in.
-It's my mistake on this point, the adapter *is *actually USB3. It's newer than it looks, that's for sure. As soon as you mentioned the discrepancy in the speed something clicked in my brain and I checked.
-For the hdparms, I don't know what you mean by this and I also don't think it's relevant when I'm still troubleshooting the drives separately.

Thanks for the reply. If you want any more clarification please ask. Basically the problem as it stands now is: I have two drives that have normal read/write speeds in Windows but meh read and terrible write speeds in Ubuntu.

**EDIT**

Here's the full SMART printout for one of these drives:

```
=== START OF INFORMATION SECTION ===Model Family:     HGST Travelstar 5K1000
Device Model:     HGST HTS541010A9E680
Serial Number:    J88000HW0AHS1B
LU WWN Device Id: 5 000cca 8dac4c6cf
Firmware Version: JA0OA7J0
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Form Factor:      2.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 6
SATA Version is:  SATA 2.6, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Thu Aug 15 23:37:32 2019 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (   45) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 236) minutes.
SCT capabilities:              (0x003d) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   188   188   033    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       11
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   100   100   000    Old_age   Always       -       14
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       11
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       7
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       25
194 Temperature_Celsius     0x0002   200   200   000    Old_age   Always       -       30 (Min/Max 22/32)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0
223 Load_Retry_Count        0x000a   100   100   000    Old_age   Always       -       0


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

And here's the same drive's hdparm results

```
/dev/sdf: Timing cached reads:   17104 MB in  1.99 seconds = 8576.11 MB/sec
 Timing buffered disk reads:  36 MB in  3.05 seconds =  11.81 MB/sec
```

And finally here's three dd operations, showing how the data rate falls off exponentially as you increase the block count. In these three tests, the count was increased by 1 each time. We can also completely ignore the cache idea I had earlier as the drive is dropping off in speed well before it's hitting the 8MB cache.
```
papkee@axel-base:~$ sudo dd bs=8k count=**167** if=/dev/zero of=/dev/sdf167+0 records in
167+0 records out
1368064 bytes (1.4 MB, 1.3 MiB) copied, 0.0109313 s, [B]125 MB/s
[/B]
papkee@axel-base:~$ sudo dd bs=8k count=**168** if=/dev/zero of=/dev/sdf
168+0 records in
168+0 records out
1376256 bytes (1.4 MB, 1.3 MiB) copied, 0.0390592 s, [B]35.2 MB/s
[/B]
papkee@axel-base:~$ sudo dd bs=8k count=**169** if=/dev/zero of=/dev/sdf
169+0 records in
169+0 records out
1384448 bytes (1.4 MB, 1.3 MiB) copied, 1.31557 s, **1.1 MB/s**

```

---

### Post by TheFu on 2019-08-16
The drive timing tests seem slow. One of my WD-Blue 1TB HDDs:
```
$ sudo hdparm -tT /dev/sda
/dev/sda:
 Timing cached reads:   18536 MB in  2.00 seconds = 9278.04 MB/sec
 Timing buffered disk reads: 532 MB in  3.00 seconds = 177.31 MB/sec

```
Whenever I setup my SW RAID with new disks, I always rerun the tuning.  Every disk on each controller is a little different and the cache on each disk matters.
```
sudo /sbin/blockdev --setra 8196 /dev/sda
```
Try with different read-ahead values - 256, 512, 1K, 2K, 4K, 8K ... and rerun the read timing tests after each change to optimize reads.

I don't think I'd write directly to the disk device. You'll miss out on the extra buffering that Linux provides in the file system and LVM, if you use that.  My results on that same cheap WD-blue HDD
```
Drives:    HDD Total Size: 1512.3GB (31.7% used)
           ID-1: /dev/sda model: **WDC_WD10EZEX** size: 1000.2GB

```
:
```
$ sudo dd bs=8k count=169 if=/dev/zero of=./TEST
169+0 records in
169+0 records out
1384448 bytes (1.4 MB, 1.3 MiB) copied, 0.0021771 s, 636 MB/s

```
I use LVM+ext4.  These are all SATA3 connected. The disk buffers help greatly.

Could the reason the disk was returned be terrible performance? 

I don't know if this is a religious war for you or you just need a solution ASAP. The easy solution to poor HDD performance is to use SSDs.  If this is religious war, then I'd try an older kernel, boot from different distros and see if that matters.  If that doesn't help, I'd replace each specific component one at a time and test. HDD, cable, power supply, HBA to start.

---

### Post by papkee on 2019-08-17
> **TheFu said:**
> 

I don't know if this is a religious war for you or you just need a solution ASAP. The easy solution to poor HDD performance is to use SSDs.  If this is religious war, then I'd try an older kernel, boot from different distros and see if that matters.  If that doesn't help, I'd replace each specific component one at a time and test. HDD, cable, power supply, HBA to start.

I think it's more of a "I have these drives and I'd rather use them then buy more" but at the end of the day if I don't find a relatively straightforward solution they'll end up going in the spares bin anyway. Someone on stackoverflow suggested it could be a bios version thing on the motherboard since it is a bit older (Supermicro X8SIL) so I'll probably try updating that along with doing the tuning you recommended.

At the end of the day it's the fact that they work fine in Windows that's bothering me the most. I'm thinking the bios idea might be on to something - could be a weird interaction between the specific drive type and the motherboard/OS.

---

### Post by TheFu on 2019-08-17
I understand completely.  Have you looked for new firmware for the HDDs?  There have been some really poor performance from early firmwares before.  Definitely look for new BIOS and firmware for the MB chips too.

I could see the MB drivers, controller drivers and disks having performance if they aren't all current with each other.

Also, did you verify that the partitions weren't mis-aligned?  When it comes to storage, I'm firmly in the ALWAYS use some partition group, even for RAID disks.  The testing wrote to the full device, not a partition, but in real use, you'll have a file system and partition and possible LVM or ZFS doing volume management, each has built-in methods to make storage seem faster than it is.

---

### Post by papkee on 2019-08-17
I've done the same dd tests above on a basic partition created using fdisk. The results were the same.

Additional information that may or may not be relevant - it seems the latest BIOS version (1.2) does not work properly with my board. When it's installed, I'm unable to access the BIOS menu and it will not boot using my OS drive. The only way to get anything other than a black screen with 1.2 is to remove all hard drives and use a DOS stick to flash the BIOS back to 1.1. Then the system once again works normally. Why that is, I have no clue.

In regards to drive firmware - I was unable to find any at all. The model of these drives is **HGST 0J22413** if you can find anything I couldn't. Updating firmware is always worth a shot.

Now that my system is back in a usable state I will try the other suggestions you've given and report back with any new findings.

---

### Post by papkee on 2019-08-18
I think something's up here. I created ext4 systems on both drives and mounted them to /media/tmp and /media/tmp2. However these results lead me to believe that it's still just writing to the ssd that is on / instead of the actual drives themselves. Pretty sure you can't exactly hit 1GB/s with a 5400rpm drive.

Drive 1:
```
sudo dd bs=8k count=1000 if=/dev/zero of=/media/tmp/test
1000+0 records in
1000+0 records out
8192000 bytes (8.2 MB, 7.8 MiB) copied, 0.00743362 s, 1.1 GB/s

```

Drive 2:
```
sudo dd bs=8k count=1000 if=/dev/zero of=/media/tmp2/test
1000+0 records in
1000+0 records out
8192000 bytes (8.2 MB, 7.8 MiB) copied, 0.00688815 s, 1.2 GB/s

```

Now I went ahead and restarted the building of the raid 1 array, just to see what happens when all is said and done. It's still very slow - currently building at 6MB/s despite the max rate set to 500MB/s. But I'll let it go, and see how it ends up when it's done in 45 hours.

---

### Post by TheFu on 2019-08-18
If you use LVM, I think you'll be amazed.  Creating an ext4 file system on LVM managed storage is instantaneous regardless of the size. I don't remember if that carries over to RAID stuff.  Also, did you tune the RAID chunk sizes?  It can make a huge difference in performance.

---

### Post by papkee on 2019-08-18
No LVM for that, just a regular old ext4 partition made with mkfs. And update for the morning, we're now 25% of the way through the resync. A short google told me that chunk size has no effect on raid 1 performance or resync speed, but maybe that was just wrong.

Not even sure if I should keep letting the raid build happen. What are the odds that after it's been resyncing at 5MB/s for two days that it will suddenly be performing great?

---

### Post by TheFu on 2019-08-18
> **papkee said:**
> No LVM for that, just a regular old ext4 partition made with mkfs. And update for the morning, we're now 25% of the way through the resync. A short google told me that chunk size has no effect on raid 1 performance or resync speed, but maybe that was just wrong.

Not even sure if I should keep letting the raid build happen. What are the odds that after it's been resyncing at 5MB/s for two days that it will suddenly be performing great?

In know that chunk size mattered when I first built my RAID, but it was RAID5 then.  Is chunk size the same as stripe size?  If it is, then you are correct, unless you do RAID10.  LVM makes all sorts of things better and more capable.  If you are doing RAID, then I'd do LVM too.  Actually, LVM used mdadm code to make RAID, so you don't need to use mdadm anymore directly.

Whether you should or shouldn't start over is up to you. I have no useful guidance.  My SW-RAID systems haven't had any issues in so many years I can't remember.  I did have a Seagate HDD fail, but I was too busy being happy that the last cheap Seagate was out-o-here to complain.  It was under warranty, but I didn't bother.  Replaced it with a Toshiba something.

Well - gotta go help out at the LUG now.  Good luck.

---

### Post by papkee on 2019-08-28
Just an update for anyone wondering, after a week of the drives seeming to behave fine this morning my nextcloud setup slowed to a crawl. CPU IOWait was going crazy. The raid array stopped responding and I couldn't unmount it or stop it. A hard reset of the server let me back in and I was able to unmount the array and stop it. Normalcy was restored but it seems like these drives are still being problem children for me. SMART data is still showing no problem of course.

Will have to do some further testing but I threw a spare single 500GB WD drive in one of the empty bays and it's behaving fine, so once again it seems like it's not external hardware causing issues.

---

### Post by papkee on 2019-09-03
Hi again everyone.

Still struggling with this issue. I acquired two fresh HGST 1TB drives and they seem to be exhibiting the same behavior, which leads me to believe that this is a problem with the Ubuntu system itself.

As a quick test this afternoon, I used a spare 500GB Samsung 5400RPM drive, made a single partition and an ext4 filesystem, and was able to achieve speeds of around 20-30MB/s using dd with oflag=direct. Using the HGST drives in the same bay with the same test setup, I was only able to reach speeds of 6-7MB/s.

My conclusion is that Ubuntu 18.04, or at least the driver for the motherboard's SATA controller, has a strange conflict with these HGST drives. Again, with two different models of HGST drive (0J22413 and 0J38083) the same issue exists. Both test HGST drives were fresh drives at the beginning of testing and show no SMART errors. The only difference I can see is that both HGST drives are AF (Advanced Format) drives which I suppose could be causing issues since my motherboard is somewhat older (Supermicro X8SIL).

Any help would be greatly appreciated. I've had zero issues with HGST drives on other systems, and other manufacturer's drives work fine on this system. There's a strange conflict between these drives and my system and I don't even know where to start troubleshooting this strange issue.

Here's a quick hdparm for the working 500GB samsung drive:
```

 Model=SAMSUNG HM501II, FwRev=2AJ10003, SerialNo=S267J90ZB33696
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=976773168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-0,1,2,3,4,5,6,7

```

And for the nonworking HGST drive:
```

 Model=HGST HTS541010A9E680, FwRev=JA0OA7J0, SerialNo=J88000D8GD5ABD
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-2,3,4,5,6,7

```

Not sure if that's useful to anyone but as far as I can tell they're practically identical. Like I said before as far as I can tell the SMART data is also perfect for all these drives.

---

### Post by TheFu on 2019-09-04
Have you tried using a different disk controller?
Also, if the partitions are aligned on sector boundaries (4K), all access can be 30% slower.  Basically, I start the first partition at 1MB on the disk.

In theory, gparted and **parted -a optimal** will do this automatically for new partitioning.  fdisk on 16.04 and later claims to align too, according to the manpage:
```
       All partitioning is driven by  device  I/O  limits  (the  topology)  by
       default.   fdisk  is  able  to optimize the disk layout for a 4K-sector
       size and use an alignment offset on modern devices for MBR and GPT.  It
       is  always a good idea to follow fdisk's defaults as the default values
       (e.g. first and last partition sectors) and partition  sizes  specified
       by  the  +<size>{M,G,...}  notation are always aligned according to the
       device properties.
```

---

