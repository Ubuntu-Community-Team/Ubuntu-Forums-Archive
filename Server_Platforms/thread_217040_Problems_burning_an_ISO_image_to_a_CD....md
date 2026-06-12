---
title: "Problems burning an ISO image to a CD..."
date: 2006-07-16
forum: Server Platforms
---

### Post by dustparticle on 2006-07-16
I'm trying to burn an ISO image to a CD with cdrecord. I give the following command:
```

sudo cdrecord -v /dev/hdd name_of_file.iso
```

I get the following error:

*Track 01:    0 MB written.cdrecord: Input/output error. read error on input fileWriting  time:    4.309s*

Output from cdrecord:

```
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
cdrecord: Warning: Running on Linux-2.6.15-26-server
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
TOC Type: 1 = CD-ROM
scsidev: '/dev/cdrw'
devname: '/dev/cdrw'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   :
Vendor_info    : '_NEC    '
Identifikation : 'DVD_RW ND-1300A '
Revision       : '1.08'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x001B
Profile: 0x001A
Profile: 0x0014
Profile: 0x0013
Profile: 0x0011
Profile: 0x0010
Profile: 0x000A
Profile: 0x0009 (current)
Profile: 0x0008 (current)
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Drive buf size : 1345536 = 1314 KB
FIFO size      : 4194304 = 4096 KB
Track 01: data  unknown length
Track 02: data   692 MB
Total size:      795 MB (78:48.09) = 354607 sectors
Lout start:      795 MB (78:50/07) = 354607 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 6
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type C, low Beta category (C-) (6)
  ATIP start of lead in:  -11231 (97:32/19)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 27
Manufacturer: Prodisc Technology Inc.
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 5239
Starting to write CD/DVD at speed 16 in real TAO mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Performing OPC...
Starting new track at sector: 0
Track 01:    0 MB written.cdrecord: Input/output error. read error on input fileWriting  time:    4.309s
cdrecord: fifo had 64 puts and 1 gets.
cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

```


I have tried several times with different ISO files. I also tried changing the permissions of the ISO file.


Suggestions are welcome

Thanks.

---

