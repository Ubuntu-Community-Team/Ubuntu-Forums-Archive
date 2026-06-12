---
title: "Need help with burning"
date: 2011-07-02
forum: Ubuntu Studio
---

### Post by landon12686 on 2011-07-02
I need help with burning cds and dvds. I am fairly new to linux and am currently running the newest ubuntu studio os. I have done away with wodim and installed original cdrecord already and still no luck.
Any help at all would be greatly appreciated and I can provide any additional info if needed as well... Like I said I am fairly new and do not know much but I have used other linux distros and been able to burn without a problem so I do not believe it is my burner or cds/dvds. After installing linux mint the errors started happening so I have since tried installing other distros with no better luck. Here is the latest error message I got from k3b

Devices
-----------------------
ATAPI DVD A  DH20A4P 9P57 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

System
-----------------------
K3b Version: 2.0.2
KDE Version: 4.6.2 (4.6.2)
QT Version:  4.7.2
Kernel:      2.6.38-8-generic

Used versions
-----------------------
cdrecord: 3.0

cdrecord
-----------------------
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
SCSI buffer size: 64512
/usr/bin/cdrecord: Warning: Cannot read drive buffer.
/usr/bin/cdrecord: Warning: The DMA speed test has been skipped.
Text len: 1368
Cdrecord-ProDVD-ProBD-Clone 3.00 (i686-pc-linux-gnu) Copyright (C) 1995-2010 J&#65533;rg Schilling
TOC Type: 0 = CD-DA
Using libscg version 'schily-0.9'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'ATAPI   '
Identifikation : 'DVD A  DH20A4P  '
Revision       : '9P57'
Device seems to be: Generic mmc2 DVD-R/DVD-RW/DVD-RAM.
Current: CD-R
Profile: DVD+R/DL 
Profile: DVD+R 
Profile: DVD+RW 
Profile: DVD-R/DL layer jump recording 
Profile: DVD-R/DL sequential recording 
Profile: DVD-RW sequential recording 
Profile: DVD-RW restricted overwrite 
Profile: DVD-RAM 
Profile: DVD-R sequential recording 
Profile: DVD-ROM 
Profile: CD-RW 
Profile: CD-R (current)
Profile: CD-ROM 
Profile: Removable Disk 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R LAYER_JUMP
Drive buf size : 988416 = 965 KB
FIFO size      : 4194304 = 4096 KB
pregap1: -1
Track 01: audio   49 MB (04:54.50) no preemp swab copy
Track 02: audio   33 MB (03:18.06) no preemp swab copy
Track 03: audio   29 MB (02:55.52) no preemp swab copy
Track 04: audio   51 MB (05:05.04) no preemp swab copy
Track 05: audio   35 MB (03:29.64) no preemp swab copy
Track 06: audio   47 MB (04:40.64) no preemp swab copy
Track 07: audio   48 MB (04:47.74) no preemp swab copy
Track 08: audio   52 MB (05:11.06) no preemp swab copy
Track 09: audio   48 MB (04:46.68) no preemp swab copy
Track 10: audio   59 MB (05:56.29) no preemp swab copy
Total size:      455 MB (45:05.20) = 202890 sectors
Lout start:      455 MB (45:07/15) = 202890 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
Disk Is not unrestricted
Disk Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
    Capacity  Blklen/Sparesz.  Format-type  Type
      449849             2048         0x00  No Media Present or Unknown Capacity
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 156956
Forcespeed is OFF.
Starting to write CD/DVD/BD at speed 16 in real SAO mode for single session.
Last chance to quit, starting real write in 3 seconds.
   2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
/usr/bin/cdrecord: Input/output error. send opc: scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 68.803s timeout 200s
/usr/bin/cdrecord: OPC failed.
Writing  time:   73.665s
/usr/bin/cdrecord: fifo had 64 puts and 0 gets.
/usr/bin/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/cdrecord -v gracetime=2 dev=/dev/sr0 speed=16 -sao driveropts=burnfree textfile=/tmp/qt_temp.jt5267 -useinfo -audio /tmp/kde-root/k3b_audio_0_01.inf /tmp/kde-root/k3b_audio_0_02.inf /tmp/kde-root/k3b_audio_0_03.inf /tmp/kde-root/k3b_audio_0_04.inf /tmp/kde-root/k3b_audio_0_05.inf /tmp/kde-root/k3b_audio_0_06.inf /tmp/kde-root/k3b_audio_0_07.inf /tmp/kde-root/k3b_audio_0_08.inf /tmp/kde-root/k3b_audio_0_09.inf /tmp/kde-root/k3b_audio_0_10.inf

---

### Post by sgx on 2011-07-02
sometimes it's crummy support for a given media, sometimes
crummy coding, I use brasero if k3b spits out a coaster.
Occasionally I had to run the burner as root

sudo k3b

I would reinstall wodim and k3b using synaptic.
Make sure you have disk space for the buffer...

Whenever possible, I burn using TAO mode, and specify the
slowest speed possible. Ironically, I've made way more coasters this year, than in the previous 6 combined. So much for progress ;)

Cheers

---

### Post by in-dust-rial on 2011-07-02
i also have a lot of fails in the newer distributions.

when i am especially frustrated i use one of the older distributions. that works for me

---

### Post by Sef on 2011-07-02
I prefer to use GnomeBaker for burning cds and dvds.  It is available in the repositories.

---

### Post by cchhrriiss121212 on 2011-07-03
I have been using Xfburn for the last year or so on a variety of distros, in that time I have burned ~20 DVDs/CDs/data with no failures at all. The interface is also one of the best I have seen.
I don't know how brasero and k3b manage to fall short for so many users, while still remaining popular choices.

---

### Post by landon12686 on 2011-07-04
Thanks for all the suggestions. I have kinda lucked out in the fact that no program I have used lately has even made it to the write process it always fails before and spits the cd out leaving it completely blank and at least still usable which is a good thing or I would have wasted well over 100 cds and dvds.

---

### Post by jejeman on 2011-07-04
Unfortunately burning is often an issue in Ubuntu. In my experience 10.04 is better to burn from nautilus, in 11.04 is better to burn from brasero. I've recently burned 2 dvd's in 11.04, and that was real hell. More than 30 min. for each, plus one damaged.
I also want to know why is so hard to burn discs on ubuntu (linux)?

---

### Post by landon12686 on 2011-07-10
I have just burned several live dvds through k3b but still no luck with the cds. So it seems like as long as I am burning an iso file to a blank dvd my system handles it without a problem. I am going to try yet another brand of cdr to see if that is the problem although I have used the same type of cdrs many of times before without a problem.

---

