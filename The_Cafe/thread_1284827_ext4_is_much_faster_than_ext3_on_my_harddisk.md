---
title: "ext4 is much faster than ext3 on my harddisk"
date: 2009-10-07
forum: The Cafe
---

### Post by afeasfaerw23231233 on 2009-10-07
Yesterday I reinstall the whole system and format the disk as ext3. Although hdparm -tT shows similar values (~130MB/s) as my previous ext4, practically the read/write speed on ext3 seldom exceeds 70MB/s. But in ext4 it can always get more than 100MB/s. ext3 is particularly slow when coping with small files. Sometimes it would drop to 30MB/s. But in ext4 the speed rarely drops below 50MB/s.

---

### Post by Sean Moran on 2009-10-07
Thanks for the inspiration mate!  I will try out ext4 tomorrow! 
:popcorn:

---

### Post by rudihawk on 2009-10-07
I've running ext4 for a long time now without a problem. Yes, it is faster than ext3.

---

### Post by siimo on 2009-10-07
Is it stable enough to be used in production environment yet?  I think I will wait for 2-3 years more till it becomes more mainstream.

---

### Post by toupeiro on 2009-10-07
One of the things I've noticed as a sysadmin about EXT4 that I really like over EXT3 is how fast ACL changes are applied recursively on huge directory listings.  It's almost instantaneous, whereas EXT3 did the traditional directory crawl, touching everything one by one.

---

### Post by afeasfaerw23231233 on 2009-10-07
But is this speed for ext3 normal? It seems that it is far too slow while compare to ext4.

My harddisk is Seagate 7200.12 SATAII 16MB buffer with NCQ but it gives no notible difference while compared to my old 7200.9 ATA100 8MB buffer harddisk when both are ext3. It really got prominant performance boot in ext4. I have test ext4 with the old harddisk too, the gain is only marginal.

ext4 caused random freeze on my system while deleting a lot small files so I compiled my kernel but it turned out to be a mess (n00b!). After all frustrations I reinstalled 9.04 and formatted the drive as ext3. I heard that 2.6.28 x86-64 has some problem for ext4 but it has been fixed at 2.6.30. Initially I want to try 9.10 but only beta is available and the official version is not out yet.

Hope that the bug has been fixed on 9.10. Now I have no desire to upgrade as my system is stable.

---

### Post by Sean Moran on 2009-10-07
> **afeasfaerw23231233 said:**
> But is this speed for ext3 normal? It seems that it is far too slow while compare to ext4.

My harddisk is Seagate 7200.12 SATAII 16MB buffer with NCQ but it gives no notible difference while compared to my old 7200.9 ATA100 8MB buffer harddisk when both are ext3. It really got prominant performance boot in ext4. I have test ext4 with the old harddisk too, the gain is only marginal.

ext4 caused random freeze on my system while deleting a lot small files so I compiled my kernel but it turned out to be a mess (n00b!). After all frustrations I reinstalled 9.04 and formatted the drive as ext3. I heard that 2.6.28 x86-64 has some problem for ext4 but it has been fixed at 2.6.30. **Initially I want to try 9.10 but only beta is available and the official version is not out yet.**

Hope that the bug has been fixed on 9.10. Now I have no desire to upgrade as my system is stable.
A little like you mention, I waited until this month for the Beta before upgrading to 9.10 and it has worked well enough for almost a week now, so please be careful about your hardware requirements and don't take chances, but I think it's ready enough to use with ext3, and by that I would assume that ext4 is better if not the same, having never used that format before.
Please don't take this advice as gospel as I am using very standard sort of legacy hardware and if a Beta works anywhere, then this is one place it is likely to do so.  Anything more salubrious may not work as well as this machine.

---

### Post by speedwell68 on 2009-10-07
I have been using EXT4 since April of this year and I have to say that it has been very stable and is much faster than EXT3.

---

### Post by LookTJ on 2009-10-07
I have just converted my root(/) partition to ext4.

I had a kernel panic, which was easily recovered by the fallback and remaking the initial kernel.

---

### Post by afeasfaerw23231233 on 2009-10-07
Is it possible that NCQ or buffer is not active in ext3? 

But the information from  hdparm -iI seems to be normal
```

/dev/sda:

 Model=ST3500418AS                             , FwRev=CC35    , SerialNo=            9VM2ETR6
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=976773168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode


ATA device, with non-removable media
	Model Number:       ST3500418AS                             
	Serial Number:      9VM2ETR6
	Firmware Revision:  CC35    
	Transport:          Serial
Standards:
	Used: unknown (minor revision code 0x0029) 
	Supported: 8 7 6 5 
	Likely used: 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors:  976773168
	device size with M = 1024*1024:      476940 MBytes
	device size with M = 1000*1000:      500107 MBytes (500 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Recommended acoustic management value: 254, current value: 0
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	DOWNLOAD_MICROCODE
	    	Power-Up In Standby feature set
	    	SET_FEATURES required to spinup after power up
	    	SET_MAX security extension
	   *	Automatic Acoustic Management feature set
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	WRITE_{DMA|MULTIPLE}_FUA_EXT
	   *	64-bit World wide name
	    	Write-Read-Verify feature set
	   *	WRITE_UNCORRECTABLE_EXT command
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	   *	SATA-I signaling speed (1.5Gb/s)
	   *	SATA-II signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Phy event counters
	    	Device-initiated interface power management
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Long Sector Access (AC1)
	   *	SCT LBA Segment Access (AC2)
	   *	SCT Error Recovery Control (AC3)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
	    	unknown 206[12] (vendor specific)
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
		frozen
	not	expired: security count
		supported: enhanced erase
	80min for SECURITY ERASE UNIT. 80min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 5000c500157e1cbc
	NAA		: 5
	IEEE OUI	: c50
	Unique ID	: 0157e1cbc
Checksum: correct

```
 Now I am too lazy to switch. Surely I will use ext4 next time I need to Ubuntu. Maybe next year :)

---

### Post by Zoot7 on 2009-10-07
Nice. :D Haven't tried ext4 yet but this makes it very attractive. The whole copying several small files is painful at best.

---

### Post by RiceMonster on 2009-10-07
I'm using ext4 on both my computers. The biggest difference I notice is it does fsck A LOT faster. ext3 is very slow in that area.

---

### Post by fela on 2009-10-07
I don't think the filesystem could ever be a speed bottleneck in my system, my motherboard is so slow :(

Ah well I did get it for just £35 :P

---

