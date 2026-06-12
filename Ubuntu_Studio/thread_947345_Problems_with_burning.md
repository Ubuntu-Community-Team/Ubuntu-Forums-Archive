---
title: "Problems with burning"
date: 2008-10-14
forum: Ubuntu Studio
---

### Post by lesemi on 2008-10-14
I have never really had issues in the past until i changed my burner to a sony - since then i have upgraded from gutsy to hardy and it seems that burning CDs and DVDs has become an issue.

some days it works and others it doesn't - sometimes it burns partially, appx 50% and dies and sometimes it doesn't work at all - for both CDs and DVDs.
I know that it is not the cdr or dvdr - as they worked perfectly with my old burner before i changed it.

as well see below  -  this is the last debug report i'm getting when attempt to burn with either k3b, gnomebaker - same error:

System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
SONY DVD RW DRU-190A 1.64 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

K3bIsoImager
-----------------------
mkisofs print size result: 316889 (648988672 bytes)
Pipe throughput: 12298240 bytes read, 12293888 bytes written.

Used versions
-----------------------
mkisofs: 1.1.6
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'SONY    '
Identification : 'DVD RW DRU-190A '
Revision       : '1.64'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1867008 = 1823 KB
FIFO size      : 12582912 = 12288 KB
/usr/bin/wodim: Cannot get next writable address for 'invisible' track.
/usr/bin/wodim: This means that we are checking recorded media.
/usr/bin/wodim: This media cannot be written in streaming mode anymore.
/usr/bin/wodim: If you like to write to 'preformatted' RW media, try to blank the media first.
Speed set to 2823 KB/s
Track 01: data   618 MB        
Total size:      710 MB (70:25.21) = 316891 sectors
Lout start:      711 MB (70:27/16) = 316891 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 4
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type C, low Beta category (C-) (6)
  ATIP start of lead in:  -11559 (97:27/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 21
Manufacturer: Ricoh Company Limited
Forcespeed is OFF.
Starting to write CD/DVD at speed  16.0 in real TAO mode for multi session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Errno: 5 (Input/output error), read track info scsi sendcmd: no error
CDB:  52 01 00 00 00 FF 00 00 1C 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 06 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x06 (cannot format medium - incompatible medium) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.001s timeout 240s
/usr/bin/wodim: Cannot get next writable address for 'invisible' track.
/usr/bin/wodim: This means that we are checking recorded media.
/usr/bin/wodim: This media cannot be written in streaming mode anymore.
/usr/bin/wodim: If you like to write to 'preformatted' RW media, try to blank the media first.
/usr/bin/wodim: Cannot get next writable address.
Writing  time:    0.044s
Average write speed 999.0x.
Fixating...
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.004s timeout 480s
cmd finished after 0.004s timeout 480s
/usr/bin/wodim: Cannot fixate disk.
Fixating time:    0.007s
BURN-Free was never needed.
/usr/bin/wodim: fifo had 192 puts and 0 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=16 -tao driveropts=burnfree -overburn -multi -xa -tsize=316889s - 

mkisofs
-----------------------
316889
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.16% done, estimate finish Tue Oct 14 07:24:04 2008
  0.32% done, estimate finish Tue Oct 14 07:24:04 2008
  0.47% done, estimate finish Tue Oct 14 07:24:04 2008
  0.64% done, estimate finish Tue Oct 14 07:24:04 2008
  0.79% done, estimate finish Tue Oct 14 07:24:04 2008
  0.95% done, estimate finish Tue Oct 14 07:24:04 2008
  1.11% done, estimate finish Tue Oct 14 07:24:04 2008
  1.27% done, estimate finish Tue Oct 14 07:24:04 2008
  1.42% done, estimate finish Tue Oct 14 07:24:04 2008
  1.58% done, estimate finish Tue Oct 14 07:24:04 2008
  1.74% done, estimate finish Tue Oct 14 07:24:04 2008
  1.90% done, estimate finish Tue Oct 14 07:24:04 2008

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid Mamma Mia_01_01 -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-sener/k3bJn39Xb.tmp -rational-rock -hide-list /tmp/kde-sener/k3bV5kXib.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-sener/k3bkhtPRb.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-sener/k3b5H5K0a.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid Mamma Mia_01_01 -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-sener/k3b3if76b.tmp -rational-rock -hide-list /tmp/kde-sener/k3bk1mBCa.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-sener/k3bAfKbcb.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-sener/k3b8MLjca.tmp

---

### Post by lesemi on 2008-10-15
Hi - i have tried with gnome baker and here is the result of the error.
As well - this burner is used on my windows partition as well - and it works without a problem with my cdr and dvdrs - thus eliminating the hardware and media issue.
anybody have an idea?

wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'SONY    '
Identification : 'DVD RW DRU-190A '
Revision       : '1.64'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1867008 = 1823 KB
FIFO size      : 12582912 = 12288 KB
wodim: Cannot get next writable address for 'invisible' track.
wodim: This means that we are checking recorded media.
wodim: This media cannot be written in streaming mode anymore.
wodim: If you like to write to 'preformatted' RW media, try to blank the media first.
Speed set to 2823 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Writing  time:    0.044s
Average write speed 999.0x.
Fixating...
Errno: 5 (Input/output error), read track info scsi sendcmd: no error
CDB:  52 01 00 00 00 FF 00 00 1C 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 06 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x06 (cannot format medium - incompatible medium) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.001s timeout 240s
wodim: Cannot get next writable address for 'invisible' track.
wodim: This means that we are checking recorded media.
wodim: This media cannot be written in streaming mode anymore.
wodim: If you like to write to 'preformatted' RW media, try to blank the media first.
wodim: Cannot get next writable address.
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.005s timeout 480s
cmd finished after 0.005s timeout 480s
Fixating time:    0.007s
wodim: Cannot fixate disk.
BURN-Free was never needed.
wodim: fifo had 192 puts and 0 gets.
wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

---

