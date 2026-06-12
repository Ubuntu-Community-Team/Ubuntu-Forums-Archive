---
title: "Advanced Sector Warning using WD10EADS?"
date: 2011-05-09
forum: Server Platforms
---

### Post by NeilR on 2011-05-09
Using Ubuntu Server 10.04 LTS and formatting drives using WebMin I am getting the following warning when formatting WD10EADS drives.  I thought this warning only applied to the newer Advanced Format 4K sector drives like the EARS series?  Is this a false warning/bug?

I did not get this warning when formatting a WD1001FALS (Black) drive.  I also think I did not get it the last time formatted one of the two WD10EADS drives.  So it may not be consistent although it happened at least most of the times I formatted the drives (had another issue which kept me reformatting to test).

I have not seen any unusual performance issues.  The drives are moving data at 40-50MB/s across my network.  Just curious about this.  Thanks!


```
Executing command mkfs -t ext3 -q /dev/sdd1 ; partprobe ..
/dev/sdd1 alignment is offset by 512 bytes.
This may result in very poor performance, (re)-partitioning suggested.

```

Edit:  fdisk -lu for each drive.  sdd indicates a problem but sdc and sdd are both WD10EADS although different models.  Although this last format was in Linux Raid format for a Raid 5 test, I got the same error on one drive when formatting it for Linux as Ext4 for a prior test.

```
neil@ANTECUBSV:/mnt$ sudo fdisk -lu /dev/sdb

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x341c3f45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953520064   976760001   fd  Linux raid autodetect
neil@ANTECUBSV:/mnt$ sudo fdisk -lu /dev/sdc

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x326c6521

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  1953520064   976760001   fd  Linux raid autodetect
neil@ANTECUBSV:/mnt$ sudo fdisk -lu /dev/sdd

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd8df0e95

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63  1953520064   976760001   fd  Linux raid autodetect
**Partition 1 does not start on physical sector boundary.**
neil@ANTECUBSV:/mnt$
```

Edit: and smartctl -a for each drive, redacting Smart data

```
neil@ANTECUBSV:/mnt$ sudo smartctl -a /dev/sdb
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD1001FALS-00J7B0
Serial Number:    WD-WMATV109xxxx
Firmware Version: 05.00K05
User Capacity:    1,000,204,886,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon May  9 10:57:36 2011 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

neil@ANTECUBSV:/mnt$ sudo smartctl -a /dev/sdc
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD10EADS-00L5B1
Serial Number:    WD-WCAU4709xxxx
Firmware Version: 01.01A01
User Capacity:    1,000,204,886,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon May  9 10:57:36 2011 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


neil@ANTECUBSV:/mnt$ sudo smartctl -a /dev/sdd
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD10EADS-11M2B1
Serial Number:    WD-WCAV5436xxxx
Firmware Version: 80.00A80
User Capacity:    1,000,204,886,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon May  9 11:00:56 2011 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
```

---

### Post by NeilR on 2011-05-09
I re-googled the model and sub-model and found [this]("http://community.wdc.com/t5/Desktop/2-WD10EADS-drives-1-with-512B-sector-1-with-4096B-sector/td-p/45368").  So I'm not the only one confused.  I'd never heard of 4k sector EADS drives and I haven't bought a 1TB drive in quite awhile.  I attached an hdparm of the drive, which might be better.

I guess I have a 4K drive whether I like it or not?


```
neil@ANTECUBSV:/mnt$ sudo hdparm -I /dev/sdd
[sudo] password for neil:

/dev/sdd:

ATA device, with non-removable media
        Model Number:       WDC WD10EADS-11M2B1
        Serial Number:      WD-WCAV5436xxxx
        Firmware Revision:  80.00A80
        Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
Standards:
        Supported: 8 7 6 5
        Likely used: 8
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  268435455
        LBA48  user addressable sectors: 1953525168
        Logical  Sector size:                   512 bytes
        Physical Sector size:                  4096 bytes
        Logical Sector-0 offset:                  0 bytes
        device size with M = 1024*1024:      953869 MBytes
        device size with M = 1000*1000:     1000204 MBytes (1000 GB)
        cache/buffer size  = unknown
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 32
        Standby timer values: spec'd by Standard, with device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Recommended acoustic management value: 128, current value: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    NOP cmd
           *    DOWNLOAD_MICROCODE
                Power-Up In Standby feature set
           *    SET_FEATURES required to spinup after power up
                SET_MAX security extension
                Automatic Acoustic Management feature set
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    General Purpose Logging feature set
           *    64-bit World wide name
           *    {READ,WRITE}_DMA_EXT_GPL commands
           *    Segmented DOWNLOAD_MICROCODE
           *    Gen1 signaling speed (1.5Gb/s)
           *    Gen2 signaling speed (3.0Gb/s)
           *    Native Command Queueing (NCQ)
           *    Host-initiated interface power management
           *    Phy event counters
           *    NCQ priority information
                DMA Setup Auto-Activate optimization
           *    Software settings preservation
           *    SMART Command Transport (SCT) feature set
           *    SCT Features Control (AC4)
           *    SCT Data Tables (AC5)
                unknown 206[12] (vendor specific)
                unknown 206[13] (vendor specific)
Security:
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
                supported: enhanced erase
        204min for SECURITY ERASE UNIT. 204min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50014ee203a1ee63
        NAA             : 5
        IEEE OUI        : 0014ee
        Unique ID       : 203a1ee63
Checksum: correct
```

---

### Post by NeilR on 2011-05-10
Update:  I realized last night that this is a fairly recent drive that I got from WD in Aug 2010 when I RMA'd a much older EADS drive under warranty.  So they returned an Advance Format drive when I RMA'd a regular drive.  The label does have the standard Advanced Format blurb but I never bothered to read it.  I just popped it in a dock and ran with it.

---

### Post by rubylaser on 2011-05-10
This just means that your partition is not properly aligned to the 4K sector.  Here's how to re-align the partition with fdisk.

[http://linuxconfig.org/linux-wd-ears-advanced-format]("http://linuxconfig.org/linux-wd-ears-advanced-format")

---

### Post by ITfromScratch on 2013-04-28
This is also true with other brands. I bought a Seagate 3 TB drive recently that is also using this 4k sector technology.

---

