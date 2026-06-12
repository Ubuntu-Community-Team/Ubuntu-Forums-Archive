---
title: "mdadm slow RAID6 rebuild"
date: 2011-03-27
forum: Server Platforms
---

### Post by fermulator on 2011-03-27
Context:
 * Fresh Ubuntu 10.04.2 Server Installation 
 * Fresh Seagate ST2000DL003 (2TB) drives (4x)
 * RAID6 using mdadm

The problem is that I created the array, but the rebuild (sync) speed is rather slow.  Only getting about 13MB/s.  At the current rate, rebuild will take 2+ days...

What I did so far:
 1) Setup linux RAID partitions:
```
Disk /dev/sdl: 2000.4 GB, 2000398934016 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sdl1               1      243201  1953512001   fd  Linux raid autodetect
Disk /dev/sdm: 2000.4 GB, 2000398934016 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sdm1               1      243201  1953512001   fd  Linux raid autodetect
Disk /dev/sdn: 2000.4 GB, 2000398934016 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sdn1               1      243201  1953512001   fd  Linux raid autodetect
Disk /dev/sdo: 2000.4 GB, 2000398934016 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sdo1               1      243201  1953512001   fd  Linux raid autodetect

```

 2) Created the array
```
sudo mdadm --create --verbose /dev/md2000 --level=6 --raid-devices=4 /dev/sdl1 /dev/sdm1 /dev/sdn1 /dev/sdo1
```

 3) Monitoring the progress ... it's rather slow:
> md2000 : active raid6 sdo1[3] sdn1[2] sdm1[1] sdl1[0]
      3907023872 blocks level 6, 64k chunk, algorithm 2 [4/4] [UUUU]
      [>....................]  resync =  1.7% (33775612/1953511936) finish=2345.3min speed=13642K/sec

I've already tried tweaking the speed settings:
> fermulator@fermmy-server:/mnt$ cat /sys/block/md2000/md/sync_speed_min
100000 (system)
fermulator@fermmy-server:/mnt$ cat /sys/block/md2000/md/sync_speed_max
200000 (system)

Also I increased the stripe cache size (which actually ~doubled my speed from 7MB to 13MB)
> fermulator@fermmy-server:/mnt$ cat /sys/block/md2000/md/stripe_cache_active 
7440
fermulator@fermmy-server:/mnt$ cat /sys/block/md2000/md/stripe_cache_size
8192

Here's an output of sysstat:
```
08:11:48 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
08:12:48 PM     all      0.30      0.00      8.43      0.39      0.00     90.87
08:12:48 PM       0      0.25      0.00     13.87      0.47      0.00     85.42
08:12:48 PM       1      0.34      0.00      3.24      0.34      0.00     96.09

08:11:48 PM       tps      rtps      wtps   bread/s   bwrtn/s
08:12:48 PM    402.25    145.18    257.07 130679.07  48747.07

08:11:48 PM   runq-sz  plist-sz   ldavg-1   ldavg-5  ldavg-15
08:12:48 PM         1       243      2.11      2.10      1.96

08:11:48 PM       DEV       tps  rd_sec/s  wr_sec/s  avgrq-sz  avgqu-sz     await     svctm     %util
08:12:48 PM       sda      0.00      0.00      0.00      0.00      0.00      0.00      0.00      0.00
08:12:48 PM       sdb      0.00      0.00      0.00      0.00      0.00      0.00      0.00      0.00
08:12:48 PM       sdc      0.00      0.00      0.00      0.00      0.00      0.00      0.00      0.00
08:12:48 PM       sdd      0.00      0.00      0.00      0.00      0.00      0.00      0.00      0.00
08:12:48 PM       sde      0.80      0.00      8.67     10.83      0.01     12.92      8.50      0.68
08:12:48 PM    md1002      0.00      0.00      0.00      0.00      0.00      0.00      0.00      0.00
08:12:48 PM    md1001      0.92      0.00      6.80      7.42      0.00      0.00      0.00      0.00
08:12:48 PM       sdf      0.80      0.00      8.67     10.83      0.01      9.25      9.25      0.74
08:12:48 PM       sdh      0.00      0.00      0.00      0.00      0.00      0.00      0.00      0.00
08:12:48 PM       sdk      0.00      0.00      0.00      0.00      0.00      0.00      0.00      0.00
08:12:48 PM       sdi      0.00      0.00      0.00      0.00      0.00      0.00      0.00      0.00
08:12:48 PM       sdg      0.00      0.00      0.00      0.00      0.00      0.00      0.00      0.00
08:12:48 PM       sdj      0.00      0.00      0.00      0.00      0.00      0.00      0.00      0.00
08:12:48 PM    md1000      0.00      0.00      0.00      0.00      0.00      0.00      0.00      0.00
08:12:48 PM     md250      0.00      0.00      0.00      0.00      0.00      0.00      0.00      0.00
08:12:48 PM       sdl    100.07  32819.20  16273.07    490.60     74.07    743.68      9.99    100.00
08:12:48 PM       sdm     99.03  32445.87   8114.00    409.56     50.47    509.13     10.10    100.00
08:12:48 PM       sdn     99.38  32776.13  16089.60    491.69    112.22   1123.66     10.06    100.00
08:12:48 PM       sdo    101.25  32637.87   8244.13    403.77     77.24    775.83      9.88    100.00
08:12:48 PM    md2000      0.00      0.00      0.00      0.00      0.00      0.00      0.00      0.00

```

At some point /dev/sdo was more utilized than the other drives in /dev/md2000 array, (but not in the above snapshot).

Just for fun, I compared smart control output between two drives, but they seem OK.

```
fermulator@fermmy-server:~$ sudo smartctl -A /dev/sdo
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   115   100   006    Pre-fail  Always       -       94973496
  3 Spin_Up_Time            0x0003   092   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       8
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   253   030    Pre-fail  Always       -       358964
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       3
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       8
183 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
184 Unknown_Attribute       0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   061   061   045    Old_age   Always       -       39 (Lifetime Min/Max 25/39)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       7
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       8
194 Temperature_Celsius     0x0022   039   040   000    Old_age   Always       -       39 (0 19 0 0)
195 Hardware_ECC_Recovered  0x001a   030   030   000    Old_age   Always       -       94973496
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       190773857353731
241 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       20889848
242 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       69249573

```

Compare that to a drive that doesn't appear over-utilized:
```
fermulator@fermmy-server:~$ sudo smartctl -A /dev/sdm
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   116   100   006    Pre-fail  Always       -       101115976
  3 Spin_Up_Time            0x0003   092   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       8
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   253   030    Pre-fail  Always       -       382410
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       3
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       8
183 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
184 Unknown_Attribute       0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   061   061   045    Old_age   Always       -       39 (Lifetime Min/Max 25/39)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       7
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       8
194 Temperature_Celsius     0x0022   039   040   000    Old_age   Always       -       39 (0 20 0 0)
195 Hardware_ECC_Recovered  0x001a   031   031   000    Old_age   Always       -       101115976
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       108344845008899
241 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       22399368
242 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       76051829

```

Based on smartctl_diff.png, I don't see any obvious issues between the two drives.

Any ideas what my problem is?

---

### Post by disabledaccount on 2011-03-28
There is not much sense in rebuilding empty array - use "--assume-clean" option.
Configure write intent bitmap

Can you tell what SATA controller You are using? 
What is the result from fdisk **-ul** /dev/sd[lmno] - I can't read CHS :)

---

### Post by fermulator on 2011-03-28
> **tomazzi said:**
> There is not much sense in rebuilding empty array - use "--assume-clean" option.
Configure write intent bitmap

Can you tell what SATA controller You are using? 
What is the result from fdisk **-ul** /dev/sd[lmno] - I can't read CHS :)

Can I stop the array, wipe it, then restart the create with "--assume-clean"?  I presume it would be more efficient, given the current ETA is still 1000minutes remaining?

RE "configure write intent bitmap"
I didn't know what that meant, so googled, and found [https://raid.wiki.kernel.org/index.php/Write-intent_bitmap](https://raid.wiki.kernel.org/index.php/Write-intent_bitmap)

Tried with, but failed:
```
fermulator@fermmy-server:~$ sudo mdadm --grow --bitmap=internal --verbose /dev/md2000
mdadm: failed to set internal bitmap.

```
/var/log/messages shows:
> Mar 28 12:00:09 fermmy-server kernel: [69290.539010] md: couldn't update array info. -16

The controller I'm using is the Intel SASUC8I:
```
           *-scsi
                description: SCSI storage controller
                product: SAS1068E PCI-Express Fusion-MPT SAS
                vendor: LSI Logic / Symbios Logic
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: scsi18
                version: 08
                width: 64 bits
                clock: 33MHz
                capabilities: scsi pm pciexpress msi msix bus_master cap_list rom scsi-host
                configuration: driver=mptsas latency=0
                resources: irq:16 ioport:e000(size=256) memory:d0610000-d0613fff memory:d0600000-d060ffff memory:d0400000-d05fffff(prefetchable)
```


```
fermulator@fermmy-server:~$ sudo fdisk -ul /dev/sd[lmno]

Disk /dev/sdl: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4c11e7bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdl1              63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sdm: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x53ed25f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdm1              63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sdn: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xce514e52

   Device Boot      Start         End      Blocks   Id  System
/dev/sdn1              63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sdo: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x13f4af7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdo1              63  3907024064  1953512001   fd  Linux raid autodetect

```

---

### Post by rubylaser on 2011-03-28
To turn on write intent bitmapping, your RAID volume must be configured with a persistent superblock and has to be fully synchronized.  I'd hate to have you recreate your array, because at some point those disks need to be synchronized, so why don't you try to increase your speeds a little bit with this.  You'll need to run it from a terminal as the root user.

```
sudo -i
blockdev --setra 16384 /dev/sd[lmno]

echo 1024 > /sys/block/sdl/queue/read_ahead_kb
echo 1024 > /sys/block/sdm/queue/read_ahead_kb
echo 1024 > /sys/block/sdn/queue/read_ahead_kb
echo 1024 > /sys/block/sdo/queue/read_ahead_kb

echo 256 > /sys/block/sdl/queue/nr_requests
echo 256 > /sys/block/sdm/queue/nr_requests
echo 256 > /sys/block/sdn/queue/nr_requests
echo 256 > /sys/block/sdo/queue/nr_requests

# Set read-ahead.
echo "Setting read-ahead to 64 MiB for /dev/md2000"
blockdev --setra 65536 /dev/md2000

# Set stripe-cache_size for RAID5.
echo "Setting stripe_cache_size to 16 MiB for /dev/md0"
echo 16384 > /sys/block/md2000/md/stripe_cache_size

```

You should see an improvement in your sync speeds after doing this.

---

### Post by fermulator on 2011-03-28
I ran all of those commands, have waited 5 minutes, but no increase in sync speed. :-(

      
> md2000 : active raid6 sdo1[3] sdn1[2] sdm1[1] sdl1[0]
      3907023872 blocks level 6, 64k chunk, algorithm 2 [4/4] [UUUU]
      [===========>.........]  resync = 58.8% (1149730620/1953511936) finish=850.2min speed=15754K/sec

(well, compared to my original post, there is ~3MB/s increase ... but that happened yesterday after all the tweaks) -- still expecting it to be faster.

---

### Post by rubylaser on 2011-03-28
How much RAM do you have?  And, since those are advanced format hard drives, how did you align the partitions so that they're aligned to 4k sectors?

---

### Post by disabledaccount on 2011-03-28
Do You have Battery Backup Unit installed? - without this write cache is off - You can force it to work without BBU with help of LSI utility, but effect will depend on Your firmware version - its possible that You will have to upgrade or tweak it.

Secondary: partitions are not properly aligned: they should start at least on 64-block offset to gain full speed of HDD (but this is not the main reason - You can leave them as they are - jus be aware of this fact in future)

"Bitmap internal" and "--assume-clean" are working together on array creation - or, as Rubylaser mentioned You have to wait for full resync.

---

### Post by rubylaser on 2011-03-28
tomazzi, I think you might have gotten your threads crossed, the OP is using mdadm, so a BBU to enable write cache on his LSI RAID card won't really work here. I would venture a guess that a large portion of the slowness steams for partitions that aren't aligned properly.

---

### Post by Vegan on 2011-03-28
I have a few SCSI cards and any array I have used the card is the one that does the work not the OS.

At one time I had a 4 disk array with some 200 GB disks using a SATA controller. When I replaced a disk, the controller noticed and rebuilt the array before loading the OS.

---

### Post by disabledaccount on 2011-03-28
I'm more familiar with Adaptec, but AFAIR even in non-raid mode LSI takes control over WriteCache - there are separate options for each SAS/SATA channel where You can pick Write-Back, Write-Trough or OFF. I may be wrong, but its worth to check.
I've just realised that mtpsas driver could provide valuable log entries - maybe there is an answer.

I don't remember if LSI can disable loading of its bios runtime - Adaptec can - then it behaves as normal (transparent) sata/sas controller.

Performance hit from disk partition misalignment usually is not such significant - It can be - for partitions created on array (write amplification for stripes, not just single blocks)

Vegan: and I have had hot-unplugged broken harddisk from md raid-1 (nf4 chipset), repaired it and hot-plugged back - without turning off the pc. Rebuilt took several miliseconds - do You want to see the logs and pictures? (I'm allways documenting such unusual situations)

---

### Post by rubylaser on 2011-03-28
> I'm more familiar with Adaptec, but AFAIR even in non-raid mode LSI takes control over WriteCache - there are separate options for each SAS/SATA channel where You can pick Write-Back, Write-Trough or OFF.

Boy, if that's true, and I can basically add a write cache to my mdadm array like that, it will be time to upgrade my Supermicro controller :)

What controller do you use?

---

### Post by Vegan on 2011-03-28
I have used Adaptec and Promise cards and I have worked with Intel cards too for a client.

A good card is OS independent.

---

### Post by rubylaser on 2011-03-28
I'm not talking about a hardware RAID card. Tomazzi mentioned using the write cache with mdadm, and I didn't know/think this was possible. I am really am not interested in locking myself into a hardware card, and all of the heartaches that come with it in the event of a failure for my fileserver at home.  At work, I'll stick with hardware RAID cards that come with our server service agreements.

---

### Post by fermulator on 2011-03-28
Yeah so I wondered if I had to do anything special for the 4k size / sector. When I created the RAID auto detect partitions, I hoped that fdisk would have done the right thing. Can you reference a decent article on this for my reference?  Sounds like maybe I need to redo the partition setup.

The system has 2GB of RAM, and does have an APC Battery backup.

---

### Post by fermulator on 2011-03-28
I'll start by reading this: [http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=dgr-lnxw074KB-Disksdth-LX](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=dgr-lnxw074KB-Disksdth-LX)

---

### Post by fermulator on 2011-03-28
OK.  So this time around I think I have proper alignment:

I did the following (after stopping the array, and wiping the superblocks, and wiping the drives), for each disk /dev/sd[lmno],
 1) sudo fdisk /dev/sdX
 2) Disabled "DOS Compatibility" ```
c
```
 3) Enabled Sector Mode ```
u
```
 4) Created a primary partition 
    - with starting sector=2048 (default)
    - with default ending ```
n, p, 1, enter, enter
```
 5) Set type to Linux RAID autodetect (fd) ```
t, fd, enter
```
 6) Wrote changes to disk ```
w
```

Now the drives look like this:

```
fermulator@fermmy-server:~$ sudo fdisk -ul /dev/sd[lmno]

Disk /dev/sdl: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4c11e7bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdl1            2048  3907029167  1953513560   fd  Linux raid autodetect

Disk /dev/sdm: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x53ed25f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdm1            2048  3907029167  1953513560   fd  Linux raid autodetect

Disk /dev/sdn: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xce514e52

   Device Boot      Start         End      Blocks   Id  System
/dev/sdn1            2048  3907029167  1953513560   fd  Linux raid autodetect

Disk /dev/sdo: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x13f4af7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdo1            2048  3907029167  1953513560   fd  Linux raid autodetect

```

Created the array:
```
fermulator@fermmy-server:~$ sudo mdadm --create --verbose /dev/md2000 --level=6 --raid-devices=4 /dev/sdl1 /dev/sdm1 /dev/sdn1 /dev/sdo1
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: size set to 1953513472K
mdadm: array /dev/md2000 started.
```

Now the rebuild is a bit better:
```
md2000 : active raid6 sdo1[3] sdn1[2] sdm1[1] sdl1[0]
      3907026944 blocks level 6, 64k chunk, algorithm 2 [4/4] [UUUU]
      [>....................]  resync =  0.2% (4332624/1953513472) finish=1371.8min speed=23680K/sec
```


Now we're getting //better// performance.  After reading [that article]("http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=dgr-lnxw074KB-Disksdth-LX"), I think going from ~16MB/s to ~24MB/s seems about right.  (Since, the drives no longer need to read 2x sectors, write 2x sectors, for each write operation -- i.e. not quite double performance...)

Is this the best I should expect?  I don't think so.  Then I recalled, maybe the cache sizes and resync speeds I had previously tuned weren't persistent.

```
fermulator@fermmy-server:~$ cat /sys/block/md2000/md/stripe_cache_size
256
fermulator@fermmy-server:~$ cat /sys/block/md2000/md/sync_speed_max
200000 (system)
fermulator@fermmy-server:~$ cat /sys/block/md2000/md/sync_speed_min
100000 (system)
```

BOOM.  That cache_size, upped to 8192, and shazam:

```
md2000 : active raid6 sdo1[3] sdn1[2] sdm1[1] sdl1[0]
      3907026944 blocks level 6, 64k chunk, algorithm 2 [4/4] [UUUU]
      [>....................]  resync =  0.8% (15686376/1953513472) finish=788.6min speed=40951K/sec
```

Now *that's* more like it right?

---

### Post by fermulator on 2011-03-28
woa; this is useful too [http://www.avsforum.com/avs-vb/showthread.php?t=1071162&page=118](http://www.avsforum.com/avs-vb/showthread.php?t=1071162&page=118)

enabling/disabling NCQ seems to have no affect ([https://raid.wiki.kernel.org/index.php/Performance](https://raid.wiki.kernel.org/index.php/Performance))

---

### Post by rubylaser on 2011-03-29
That script you linked to is okay, other than it sets the max sync speed to 30 MB/s, which is slower than what you're getting right now :) That sync speed isn't bad, but I think you could still do a little better.

You may want up that like this...
```
echo 300000 > /sys/block/md2000/md/sync_speed_max
```

or here's a different script that works very well too.
[http://ubuntuforums.org/showthread.php?t=1494846]("http://ubuntuforums.org/showthread.php?t=1494846")

You'll need to change the MDDEV variable to match your array (md2000).

---

### Post by fermulator on 2011-03-29
So what do you think I'm missing then?  The sync_speed_max is set to 200MB/s ... and I'm not even coming close to that.

I was kind of thinking ... Seagate Green's ... 5400RPM ... 40MBs probably is expected?  You still think I can get better?

---

### Post by rubylaser on 2011-03-29
No, I got your setup crossed up with the other post in the server forum that's very similar.  40 MB/s isn't terrible sync speed.  I'll be interested to see what it can do when it's done syncing.

---

### Post by fermulator on 2011-04-01
Jizes;  As per [http://ubuntuforums.org/showthread.php?t=1719427](http://ubuntuforums.org/showthread.php?t=1719427), I had to rebuild ... it's going crazy fast this time around ... 

```
md2000 : active raid6 sdo1[3] sdn1[2] sdm1[1] sdl1[0]
      3907026944 blocks level 6, 64k chunk, algorithm 2 [4/4] [UUUU]
      [>....................]  resync =  1.5% (30989232/1953513472) finish=316.4min speed=101246K/sec
```

Seems insane ... maybe since all the bits are OK, it's not doing any writes?

---

### Post by fermulator on 2011-04-02
FYI: rsync'ing from another array to this array, I'm getting 80MB/s.

---

### Post by rubylaser on 2011-04-02
Thanks for the update.  Now that's performing much better :)

---

### Post by seabird74 on 2011-12-05
Hi, I am struggeling with the same issue. My sync is around 46Mb```
[root@server ~]# cat /proc/mdstat
Personalities : [raid0] [raid6] [raid5] [raid4]
md1 : active raid0 sdh1[0] sdi1[1]
      1953520640 blocks super 1.2 512k chunks
md0 : active raid6 sdf1[4] sdg1[5] sde1[3] sdb1[0] sdd1[2] sdc1[1]
      7814045696 blocks super 1.2 level 6, 1024k chunk, algorithm 2 [6/6] [UUUUUU]
      [==>..................]  resync = 12.1% (238250312/1953511424) finish=620.3min speed=46083K/sec
unused devices: <none>

```I have blockdev setra and stripe_size_cache set for 8192 (or16384) but don't go any higher.
My partitions should be properly aligned:```
[root@server ~]# fdisk -u -l /dev/sd[b-g]
Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
218 heads, 56 sectors/track, 320038 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000916bc
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907029167  1953513560   fd  Linux raid autodetect
Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
218 heads, 56 sectors/track, 320038 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d068b
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907029167  1953513560   fd  Linux raid autodetect
Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
218 heads, 56 sectors/track, 320038 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000353cf
   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  3907029167  1953513560   fd  Linux raid autodetect
Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
218 heads, 56 sectors/track, 320038 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007dbd7
   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048  3907029167  1953513560   fd  Linux raid autodetect
Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
218 heads, 56 sectors/track, 320038 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000377c7
   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1            2048  3907029167  1953513560   fd  Linux raid autodetect
Disk /dev/sdg: 2000.4 GB, 2000398934016 bytes
218 heads, 56 sectors/track, 320038 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0001ccde
   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1            2048  3907029167  1953513560   fd  Linux raid autodetect
[root@server ~]#
```
What am I missing????

---

### Post by a2j on 2011-12-05
my raid6 with 1.5Tb drives took hours to build. but when it was done, speeds are greater that I expected.

---

### Post by seabird74 on 2011-12-05
I don't care about the rebuild speed to be honest, but I am assuming it will say something about the actual read/write speeds

---

### Post by rubylaser on 2011-12-05
Those are not terrible rebuild speeds.  Once it's done run so dd create file and read tests to see how it goes.  Something like this.

Write Speed
```
dd if=/dev/zero of=/storage/testfile.out bs=1M count=10000
```

Read Speed
```
dd if=/storage/testfile.out of=/dev/null bs=1M
```

That will write a 10GB file (assuming you have your array mounted at /storage), and then read it back.  It will output speeds in MB/s.

---

### Post by seabird74 on 2011-12-06
Sorry, different issue took priority. Once again busy in the rebuild and still wondering. Looking at my system (Intel 8 core W3550 with 6Gb memory) it is only using 8% CPU.... 
 
Then again, maybe it is limited by the discs itself..

---

### Post by rubylaser on 2011-12-06
It's a lack of tuning that hold users back typically.  Have you tried [tuning your array]("http://ubuntuforums.org/showthread.php?t=1494846") at all?

---

### Post by seabird74 on 2011-12-07
> **rubylaser said:**
> Write Speed
```
dd if=/dev/zero of=/storage/testfile.out bs=1M count=10000
```
 
Read Speed
```
dd if=/storage/testfile.out of=/dev/null bs=1M
```

rebuild completed and ran the test. Guess I can't complaint :) (or did I run the test wrong? My array is on /dev/md0 and mounted as /storage
```
dd if=/dev/zero of=/storage/testfile.out bs=1M count=10000
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 52.6824 s, 199 MB/s

```
 
Read Speed
```
dd if=/storage/testfile.out of=/dev/null bs=1M
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 33.456 s, 313 MB/s

```

---

### Post by seabird74 on 2011-12-07
So, that brings me to my next question. Because of the rebuilt I made a backup to a temporary RAID 0 I created. I have also run this speed test on that array:```
[root@server ~]# dd if=/dev/zero of=/mnt/raid/testfile.out bs=1M count=10000
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 113.167 s, 92.7 MB/s
[root@server ~]# dd if=/mnt/raid/testfile.out of=/dev/null bs=1M
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 90.0566 s, 116 MB/s

```Why, if I copy files from one to the other (RAID0 to RAID6), do I only get 70MB/s moving speed? It should be capable of reading around 100+ should it not?

---

### Post by rubylaser on 2011-12-07
Sorry, but I have to ask a bunch of questions to figure that out :) Are the arrays in the same computer?  How are the disks connected to the computer?  What type of hardware are you using?  Have you looked at iostat and top to see how your system resources are being used?  And what command are you using to do the copying with (including any options).

Also, if you're transferring massive amounts of data, you'll notice your speeds will likely fall off.  As a good test, repeat the dd test I gave you above, but try it with a 40GB file. And, the speed test you ran has a nice blocksize, if you drop that to a smaller blocksize, you'd likely see lower speeds too.  So, when copying a bunch of little files, your throughput will typically be slower. 

```
dd if=/dev/zero of=/storage/testfile.out bs=1M count=40000
```
```
dd if=/storage/testfile.out of=/dev/null bs=1M
```

or, with a smaller blocksize...
```
dd if=/dev/zero of=/storage/testfile.out bs=64K count=160000
```
```
dd if=/storage/testfile.out of=/dev/null bs=64K
```

That should allow me to give you a better answer.

---

### Post by seabird74 on 2011-12-07
Hi, yes, they are all connected to the same computer. SATAII interface, Xeon 8 core 3.06 Ghz, 6Gb memory. The copy is done via the GUI (VNC). iostat? top?

---

### Post by rubylaser on 2011-12-07
iostat and top are command line utilities.  It's probably easier to just Google about them than me to try to explain how to use / read them.  I'd try to SSH into the box and run cp -R SOURCE DESTINATION from the command line.  Or, you could try rsync -av SOURCE DESTINATION.  I'd still be interested to see what your dd speeds look like for the 40GB example I showed and the smaller blocksize.

---

### Post by seabird74 on 2011-12-07
ok, installed iostat. In rest state:
```
[root@server init.d]# iostat
Linux 3.1.4-1.fc16.x86_64 (server.domain.com)       12/07/2011      _x86_64_        (8 CPU)
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.22    0.00    3.26    1.42    0.00   94.10
Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda              16.89       613.93       742.74   13668450   16536264
sdb              35.79      1653.67      7746.48   36817118  172466814
sdc              36.07      1659.26      7724.17   36941503  171970130
sdd              36.97      1653.20      7749.79   36806567  172540406
sde              36.68      1661.18      7726.48   36984348  172021426
sdf              29.34      1649.89      7746.28   36732909  172462366
sdg              29.39      1655.96      7724.24   36868143  171971586
sdh               0.02         0.10         0.00       2239          4
sdi               0.01         0.05         0.00       1015          0
dm-0              2.43         1.62       378.99      36032    8437760
dm-1             19.53       612.18      1227.26   13629442   27323528
md0             340.54      8088.26     29940.57  180076133  666593660
md1               0.01         0.06         0.00       1329          4

```
During the copying:```
[root@server init.d]# iostat
Linux 3.1.4-1.fc16.x86_64 (server.jaccoermers.nl)       12/07/2011      _x86_64_        (8 CPU)
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.22    0.00    3.25    1.42    0.00   94.11
Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda              16.82       610.91       738.54   13679578   16537458
sdb              35.73      1659.28      7714.86   37154846  172752347
sdc              36.01      1665.06      7692.62   37284187  172254315
sdd              36.90      1658.34      7718.09   37133803  172824699
sde              36.62      1666.15      7694.98   37308760  172307087
sdf              29.28      1655.41      7714.72   37068285  172749191
sdg              29.33      1660.92      7692.74   37191551  172257051
sdh               0.10        27.20         0.00     609047          4
sdi               0.11        27.14         0.00     607735          0
dm-0              2.41         1.61       376.82      36032    8437760
dm-1             19.46       609.17      1220.28   13640570   27324748
md0             339.77      8126.39     29816.42  181967233  667653848
md1               0.21        54.44         0.00    1218953          4

```

---

### Post by rubylaser on 2011-12-07
I don't really see much difference between those two.  Are you trying to copy from MD1 to MD0?  Also, could you please run these for me, and provide the output of each?

```
dd if=/dev/zero of=/storage/testfile.out bs=1M count=40000
```

```
dd if=/storage/testfile.out of=/dev/null bs=1M
```
or, with a smaller blocksize...

```
dd if=/dev/zero of=/storage/testfile.out bs=64K count=160000
```
```
dd if=/storage/testfile.out of=/dev/null bs=64K
```

---

### Post by seabird74 on 2011-12-07
That is what I was thinking, not much of a difference .....
 
Big blocks: (oh yeah, mounted it as /home now)
```
[root@server ~]# dd if=/dev/zero of=/home/testfile.out bs=1M count=40000
40000+0 records in
40000+0 records out
41943040000 bytes (42 GB) copied, 243.688 s, 172 MB/s
[root@server ~]# dd if=/home/testfile.out of=/dev/null bs=1M
40000+0 records in
40000+0 records out
41943040000 bytes (42 GB) copied, 150.142 s, 279 MB/s

```
 
Smaller blocks:
```
[root@server ~]# dd if=/dev/zero of=/home/testfile.out bs=64K count=160000
160000+0 records in
160000+0 records out
10485760000 bytes (10 GB) copied, 61.2613 s, 171 MB/s
[root@server ~]# dd if=/home/testfile.out of=/dev/null bs=64K
160000+0 records in
160000+0 records out
10485760000 bytes (10 GB) copied, 37.1756 s, 282 MB/s

```
 
Reran the 10Gig test to see if it is just me not rebooting in between... and came to similar results as above.

---

### Post by rubylaser on 2011-12-07
Try that same test on the other array involved in your test.  One of them is the weak link.  Or, start the test on both arrays at the same time.

---

### Post by seabird74 on 2011-12-07
It's ok, not worried about the other array ;) Only temporary storage because of the rebuilt

---

### Post by szafran on 2011-12-08
This might help a bit.
I've found this script somewhere on the interweb.
Been using it with my RAID5 (2TBx10) for about 6 months.
Works for RAID5 and RAID6 arrays.

```
#!/bin/bash
###############################################################################
#  simple script to set some parameters to increase performance on a mdadm
# raid5 or raid6. Ajust the ## parameters ##-section to your system!
#
#  WARNING: depending on stripesize and the number of devices the array might
# use QUITE a lot of memory after optimization!
#
#  27may2010 by Alexander Peganz
#  31jul211 modified by Mathias B
###############################################################################

#predkosci odbudowy
echo 2500000 > /proc/sys/dev/raid/speed_limit_max
echo 10000 >  /proc/sys/dev/raid/speed_limit_min

## parameters ##
MDDEV=md2		# e.g. md51 for /dev/md51
CHUNKSIZE=512		# in KB
BLOCKSIZE=4		# of file system in KB
NCQ=enable		# disable, enable. ath. else keeps current setting
NCQDEPTH=31		# 31 should work for almost anyone
FORCECHUNKSIZE=true	# force max sectors kb to chunk size > 512
DOTUNEFS=true		# run tune2fs, ONLY SET TO true IF YOU USE EXT[34]
RAIDLEVEL=raid5		# raid5, raid6


## code ##
# test for priviledges
if [ "$(whoami)" != 'root' ]; then
	echo $(date): Need to be root >> /#tuneraid.log
	exit 1
fi

# set number of parity devices
NUMPARITY=1
[[ $RAIDLEVEL == "raid6" ]] && NUMPARITY=2
echo "Using $NUMPARITY parity devices ($RAIDLEVEL)"
# get all devices
DEVSTR="`grep \"^$MDDEV : \" /proc/mdstat` eol"
while \
 [ -z "`expr match \"$DEVSTR\" '\(\<sd[a-z]1\[[12]\?[0-9]\]\((S)\)\? \)'`" ]
do
	DEVSTR="`echo $DEVSTR|cut -f 2- -d \ `"
done

# get active devices list and spares list
DEVS=""
SPAREDEVS=""
while [ "$DEVSTR" != "eol" ]; do
	CURDEV="`echo $DEVSTR|cut -f -1 -d \ `"
	if [ -n "`expr match \"$CURDEV\" '\(\<sd[a-z]1\[[12]\?[0-9]\]\((S)\)\)'`" ]; then
		SPAREDEVS="$SPAREDEVS${CURDEV:2:1}"
	elif [ -n "`expr match \"$CURDEV\" '\(\<sd[a-z]1\[[12]\?[0-9]\]\)'`" ]; then
		DEVS="$DEVS${CURDEV:2:1}"
	fi
	DEVSTR="`echo $DEVSTR|cut -f 2- -d \ `"
done

NUMDEVS=${#DEVS}
NUMSPAREDEVS=${#SPAREDEVS}

# test if number of devices makes sense
if [ ${#DEVS} -lt $[1+$NUMPARITY] ]; then
	echo $(date): Need more devices >> /#tuneraid.log
	exit 1
fi

echo "Found $NUMDEVS devices with $NUMSPAREDEVS spares"

# set read ahead
RASIZE=$[$NUMDEVS*($NUMDEVS-$NUMPARITY)*2*$CHUNKSIZE]   # in 512b blocks
echo read ahead size per device: $RASIZE blocks \($[$RASIZE/2/1024]MB\)
MDRASIZE=$[$RASIZE*$NUMDEVS] #tu mozna dac w pozniejszym czasie *2 na koncu
echo read ahead size of array: $MDRASIZE blocks \($[$MDRASIZE/2/1024]MB\)
blockdev --setra $RASIZE /dev/sd[$DEVS]
blockdev --setra $RASIZE /dev/sd[$SPAREDEVS]
blockdev --setra $MDRASIZE /dev/$MDDEV

# set stripe cache size
STRCACHESIZE=$[$RASIZE/8]                               # in pages per device
echo stripe cache size of devices: $STRCACHESIZE pages \($[$STRCACHESIZE*4/1024]MB\)
echo $STRCACHESIZE > /sys/block/$MDDEV/md/stripe_cache_size

# set max sectors kb
DEVINDEX=0
MINMAXHWSECKB=$(cat /sys/block/sd${DEVS:0:1}/queue/max_hw_sectors_kb)
until [ $DEVINDEX -ge $NUMDEVS ]; do
	DEVLETTER=${DEVS:$DEVINDEX:1}
	MAXHWSECKB=$(cat /sys/block/sd$DEVLETTER/queue/max_hw_sectors_kb)
	if [ $MAXHWSECKB -lt $MINMAXHWSECKB ]; then
		MINMAXHWSECKB=$MAXHWSECKB
	fi
	DEVINDEX=$[$DEVINDEX+1]
done
if [ $CHUNKSIZE -le $MINMAXHWSECKB ] && ( [ $CHUNKSIZE -le 512 ] || [[ $FORCECHUNKSIZE == "true" ]] ); then
	echo Setting max sectors KB to match chunk size
	DEVINDEX=0
	until [ $DEVINDEX -ge $NUMDEVS ]; do
		DEVLETTER=${DEVS:$DEVINDEX:1}
		echo "Set max sectors KB to $CHUNKSIZE on $DEVLETTER"
		echo $CHUNKSIZE > /sys/block/sd$DEVLETTER/queue/max_sectors_kb
		DEVINDEX=$[$DEVINDEX+1]
	done
	DEVINDEX=0
	until [ $DEVINDEX -ge $NUMSPAREDEVS ]; do
		DEVLETTER=${SPAREDEVS:$DEVINDEX:1}
		echo "Set max sectors KB to $CHUNKSIZE on $DEVLETTER"
		echo $CHUNKSIZE > /sys/block/sd$DEVLETTER/queue/max_sectors_kb
		DEVINDEX=$[$DEVINDEX+1]
	done
fi

# enable/disable NCQ
DEVINDEX=0
if [[ $NCQ == "enable" ]] || [[ $NCQ == "disable" ]]; then
	if [[ $NCQ == "disable" ]]; then
		NCQDEPTH=1
	fi
	until [ $DEVINDEX -ge $NUMDEVS ]; do
		DEVLETTER=${DEVS:$DEVINDEX:1}
		echo Setting NCQ queue depth to $NCQDEPTH on $DEVLETTER
		echo $NCQDEPTH > /sys/block/sd$DEVLETTER/device/queue_depth
		DEVINDEX=$[$DEVINDEX+1]
	done
	DEVINDEX=0
	until [ $DEVINDEX -ge $NUMSPAREDEVS ]; do
		DEVLETTER=${SPAREDEVS:$DEVINDEX:1}
		echo Setting NCQ queue depth to $NCQDEPTH on $DEVLETTER
		echo $NCQDEPTH > /sys/block/sd$DEVLETTER/device/queue_depth
		DEVINDEX=$[$DEVINDEX+1]
	done
fi

# tune2fs
if [[ $DOTUNEFS == "true" ]]; then
	STRIDE=$[$CHUNKSIZE/$BLOCKSIZE]
	STRWIDTH=$[$CHUNKSIZE/$BLOCKSIZE*($NUMDEVS-$NUMPARITY)]
	echo setting stride to $STRIDE blocks \($CHUNKSIZE KB\)
	echo setting stripe-width to $STRWIDTH blocks \($[$STRWIDTH*$BLOCKSIZE] KB\)
	echo tune2fs -E stride=$STRIDE,stripe-width=$STRWIDTH /dev/$MDDEV
	tune2fs -E stride=$STRIDE,stripe-width=$STRWIDTH /dev/$MDDEV
fi

# exit
echo $(date): Success >> /#tuneraid.log
exit 0

```

Just make sure you change the options to your needs.
Made my array about 2x faster than before.
I think if I was using a SATA3 (instead of SATA2) controller it would be even faster.

---

### Post by seabird74 on 2011-12-08
I have seen the script before. Most things I have done manually in my /etc/rc.local
 
What does the NCQ do?? and tune2fs??
 
Just wondering, what kind of read/write speeds are you getting? My bottle neck is also SATA2

---

### Post by rubylaser on 2011-12-08
SATAII supports up to 300 MB/s per device, so unless you have modern SSDs in your array, this isn't holding you back :)  Setting Native Command Queuing (NCQ) to 31 sets it to it's maximum queue length. Take a look at [this]("http://en.wikipedia.org/wiki/Native_Command_Queuing") for more info.

If you're using EXT3 or 4, tune2fs is setting your filesystem stripe and stride with to optimal values based on your mdadm array setup.  This is the same tuning script I linked to earlier.  I've used it on my own array for years.  It yields about a 30-40% improvement over default values.

---

