---
title: "comand line to burn audio cd"
date: 2009-01-05
forum: Ubuntu Studio
---

### Post by sn0m on 2009-01-05
Hi guys, does any of you know any code that can burn audio cd from command line.
I tried the following but dosen't seem to work.

sn0m@sn0m-laptop:~/Music/project$ ls
600.0  str.wav
sn0m@sn0m-laptop:~/Music/project$ file str.wav 
str.wav: RIFF (little-endian) data, WAVE audio, Microsoft PCM, 32 bit, mono 22050 Hz
sn0m@sn0m-laptop:~/Music/project$ cdrecord -v -pad speed=1 dev=0,0,0 -dao -audio -swab *.wav
TOC Type: 0 = CD-DA
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '0,0,0'
scsibus: 0 target: 0 lun: 0
WARNING: the deprecated pseudo SCSI syntax found as device specification.
Support for that may cease in the future versions of wodim. For now,
the device will be mapped to a block device file where possible.
Run "wodim --devices" for details.
Linux sg driver version: 3.5.27
Wodim version: 1.1.8
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identification : 'DVD+-RW TS-L632H'
Revision       : 'D400'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
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
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1962752 = 1916 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
FIFO size      : 12582912 = 12288 KB
wodim: Inappropriate audio coding in 'str.wav'.
sn0m@sn0m-laptop:~/Music/project$ 

I can split the file fine using gui programs like wavbraker and burn it to cd fine using brassero, but dosen't seem to get the command line going.
I can only presume that it dosen't work because the sample is 32 bit and not 16 bit?????
Any way to work around this?
Regards
Sokol

---

### Post by directhex on 2009-01-05
> **sn0m said:**
> I can only presume that it dosen't work because the sample is 32 bit and not 16 bit?????
Any way to work around this?
Regards
Sokol

Partly, yes. From "man wodim":
> The file with data for this tracks should contain stereo, 16-bit digital audio with 44100  samples/s.

32-bit 22KHz Mono is not 16-bit 44.1KHz Stereo.

---

