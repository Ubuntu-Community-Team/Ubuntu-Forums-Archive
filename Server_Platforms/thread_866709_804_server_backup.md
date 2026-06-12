---
title: "804 server backup"
date: 2008-07-22
forum: Server Platforms
---

### Post by swisstone on 2008-07-22
I am having trouble getting a dvd+rw to burn multiple times.

I have a script generate the iso then burn it.

**I create the iso using:**
mkisofs -r -R -J -l -L -o /root/ISO/BackupImage.iso -graft-points "/=/root/testbackup.sql" "/=/root/vtigerbackup.sql" "/=/var/www"


**And burn to dvd using:**
cdrecord -v speed=2 dev=/dev/scd1 /root/ISO/BackupImage.iso

[B]This works once.
But second time around the output from the burn process is:[/B]



wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
scsidev: '/dev/scd1'
devname: '/dev/scd1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   :
Vendor_info    : 'ATAPI   '
Identification : 'DVD A  DH20A1P  '
Revision       : '6X14'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x001A (DVD+RW)
Profile: 0x002B (DVD+R/DL)
Profile: 0x001B (DVD+R)
Profile: 0x001A (DVD+RW) (current)
Profile: 0x0016 (DVD-R/DL layer jump recording)
Profile: 0x0015 (DVD-R/DL sequential recording)
Profile: 0x0014 (DVD-RW sequential recording)
Profile: 0x0013 (DVD-RW restricted overwrite)
Profile: 0x0012 (DVD-RAM)
Profile: 0x0011 (DVD-R sequential recording)
Profile: 0x0010 (DVD-ROM)
Profile: 0x000A (CD-RW)
Profile: 0x0009 (CD-R)
Profile: 0x0008 (CD-ROM)
Profile: 0x0002 (Removable disk)
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE
Supported modes: PACKET SAO
Drive buf size : 1068032 = 1043 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
FIFO size      : 12582912 = 12288 KB
Track 01: data    80 MB
Total size:       92 MB (09:12.73) = 41455 sectors
Lout start:       93 MB (09:14/55) = 41455 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Blocks total: 2295104 Blocks current: 2295104 Blocks remaining: 2253649
Speed set to 5540 KB/s
Starting to write CD/DVD at speed   4.0 in real unknown mode for single session.
Last chance to quit, starting real write i   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of   80 MB written.Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 10 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x10 (medium not formatted) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 0.004s timeout 40s

write track data: error after 0 bytes
wodim: A write error occured.
wodim: Please properly read the error message above.
Writing  time:    5.071s
Average write speed  12.3x.
Fixating...
Fixating time:    0.003s
wodim: fifo had 192 puts and 1 gets.
wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
root@wilcrm:~#


**I assume from this the DVD+RW needs to be blanked or formatted but when I try to blank the DVD+RW it is not possible with the error:**


root@wilcrm:~# cdrecord blank=all -v speed=2 dev=/dev/scd1
TOC Type: 1 = CD-ROM
scsidev: '/dev/scd1'
devname: '/dev/scd1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   :
Vendor_info    : 'ATAPI   '
Identification : 'DVD A  DH20A1P  '
Revision       : '6X14'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x001A (DVD+RW)
Profile: 0x002B (DVD+R/DL)
Profile: 0x001B (DVD+R)
Profile: 0x001A (DVD+RW) (current)
Profile: 0x0016 (DVD-R/DL layer jump recording)
Profile: 0x0015 (DVD-R/DL sequential recording)
Profile: 0x0014 (DVD-RW sequential recording)
Profile: 0x0013 (DVD-RW restricted overwrite)
Profile: 0x0012 (DVD-RAM)
Profile: 0x0011 (DVD-R sequential recording)
Profile: 0x0010 (DVD-ROM)
Profile: 0x000A (CD-RW)
Profile: 0x0009 (CD-R)
Profile: 0x0008 (CD-ROM)
Profile: 0x0002 (Removable disk)
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE
Supported modes: PACKET SAO
Drive buf size : 1068032 = 1043 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Speed set to 5540 KB/s
Starting to write CD/DVD at speed   4.0 in real BLANK mode for single session.
Last chance to quit, starting real write i   0 seconds. Operation starts.
Performing OPC...
Error: this media does not support blanking, ignoring.
This drive or media does not support the 'BLANK media' command
wodim: Cannot blank disk, aborting.
root@wilcrm:~#


[B]I have tried different modes of blank=xxxx but get the same error. I have also tried 2 different brands of dvd and cannot get it to work? can anyone offer any help!?!
Do I need to use a different command to format the dvd? or is the initial iso generation causing problems? [/B]

Many Thanks
Tony

---

