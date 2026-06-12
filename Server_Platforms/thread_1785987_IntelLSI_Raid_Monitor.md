---
title: "Intel/LSI Raid Monitor"
date: 2011-06-19
forum: Server Platforms
---

### Post by Macus on 2011-06-19
Hi

I have an Ubuntu server x64 (10.04) that is running FOG for imaging
Its installed on an Intel server board (1 RU rackmount)

I configured the RAID in an Intekl based BIOS utility
which Looks similar to [This]("http://www.intel.com/support/motherboards/server/sb/img/05ctrl_bios_enabled.jpg")

Ubuntu installed and runs perfectly. however im unable to monitor the status of the drives from the OS, so Im unaware of any drive failures that may occur


I manged to install megacli but it returns blank data (along with exit code: 0x00)
Iv also tryed megactl wich says ```
unable to open device /dev/megadev0: No such file or directory
```


one of my colleagues who had used the server previously was certain that the raid was on board
the intel site also makes mention of intel using LSI products in their RAID controllers

Relevant section of dmidecode:
```
Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: Intel
	Product Name: SE7520JR22D
	Version: FRU Ver 0.01
	Serial Number: BZJR51325205
```
and lspci
```
02:03.0 RAID bus controller: LSI Logic / Symbios Logic MegaRAID (rev 01)
	Subsystem: Intel Corporation Device 0523
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr+ Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 24
	Region 0: Memory at ddff0000 (32-bit, prefetchable) [size=64K]
	Expansion ROM at de7f0000 [disabled] [size=64K]
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: megaraid
	Kernel modules: megaraid_mbox
```

Any ideas of how to monitor this?
Thanks

---

### Post by dapperdanny77 on 2011-06-20
maybe LSI MegaCli is working for you - can be found somewhere on lsi.com

```

>MegaCli -ldinfo -Lall -Aall

Adapter 0 -- Virtual Drive Information:
Virtual Drive: 0 (Target Id: 0)
Name                :
RAID Level          : Primary-5, Secondary-0, RAID Level Qualifier-3
Size                : 5.454 TB
State               : Optimal
Strip Size          : 128 KB
Number Of Drives    : 4
Span Depth          : 1
Default Cache Policy: WriteBack, ReadAheadNone, Direct, No Write Cache if Bad BBU
Current Cache Policy: WriteBack, ReadAheadNone, Direct, No Write Cache if Bad BBU
Access Policy       : Read/Write
Disk Cache Policy   : Disabled
Encryption Type     : None



Exit Code: 0x00

```

look at State which should indicate the health of your raid

---

### Post by ian dobson on 2011-06-20
Hi,

Do you see any devices in /dev maybe dev/megadev0.0?

Regards
Ian Dobson

---

### Post by dapperdanny77 on 2011-06-20
my device
```

10:00.0 RAID bus controller: LSI Logic / Symbios Logic LSI MegaSAS 9260 (rev 03)

```

it's using the megaraid_sas kernel module - OS is RedHat Enterprise 6
can't see this /dev/megadev0.0
what i see is /dev/megaraid_sas_ioctl_node

---

### Post by tgalati4 on 2011-06-20
I was able to use smartmontools to read megaraid-controlled drives:

sudo apt-get install smartmontools
man smartctl

You need a special device switch:

[http://sourceforge.net/apps/trac/smartmontools/wiki/Supported_RAID-Controllers](http://sourceforge.net/apps/trac/smartmontools/wiki/Supported_RAID-Controllers)

This works on my Dell PowerEdge 1750 rack servers and I use Dell's OMSA (transcribed from Red Hat but works under Ubuntu server) using Cacti/Nagios to get the RAID status details.

After installing smartmontools, to see drive 0:

sudo smartctl -d megaraid,0 

To run a short (nondestructive) test on drive 0:

sudo smartctl -t short -d megaraid,0

To run a long (nondestructive test--this will take several minutes):

sudo smartctl -t long -d megaraid,0

To see the results of either test or general status:

sudo smartctl -a -d megaraid,0

Once smart monitoring (smartd) is enabled, you will get messages in syslog whenever device status changes such as:


Jun 20 08:22:51 tubuntu2 apcupsd[28174]: 000.0,000.0,000.0,00.00,00.00,00.0,00.0,000.0,000.0,000.0,000.0,0
[COLOR="Red"]Jun 20 08:27:33 tubuntu2 smartd[4863]: Device: /dev/hdb, SMART Prefailure Attribute: 8 Seek_Time_Performance changed from 240 to 239 [/COLOR]
Jun 20 08:27:51 tubuntu2 apcupsd[28174]: 000.0,000.0,000.0,00.00,00.00,00.0,00.0,000.0,000.0,000.0,000.0,1
Jun 20 08:32:39 tubuntu2 sensord: Chip: it87-isa-0290
Jun 20 08:32:39 tubuntu2 sensord: Adapter: ISA adapter
Jun 20 08:32:39 tubuntu2 sensord: Algorithm: ISA algorithm
Jun 20 08:32:39 tubuntu2 sensord:   VCore 1: +1.79 V (min = +1.70 V, max = +1.87 V)
Jun 20 08:32:39 tubuntu2 sensord:   VCore 2: +2.50 V (min = +2.40 V, max = +2.61 V)
Jun 20 08:32:39 tubuntu2 sensord:   +3.3V: +3.34 V (min = +3.14 V, max = +3.47 V)
Jun 20 08:32:39 tubuntu2 sensord:   +5V: +5.03 V (min = +4.76 V, max = +5.24 V)
Jun 20 08:32:39 tubuntu2 sensord:   +12V: +12.10 V (min = +11.39 V, max = +12.61 V)

---

### Post by Macus on 2011-06-23
Thanks

The one on apt was outdated so I just compiled it

however I still get issues with the lack of /dev/megadev


```

localadmin@fog:/downloads/smartmontools-5.41$ sudo smartctl -d megaraid,0 /dev/sda
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-2.6.32-28-server] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

Smartctl open device: /dev/sda [megaraid_disk_00] failed: cannot open /dev/megaraid_sas_ioctl_node or /dev/megadev0

```

---

