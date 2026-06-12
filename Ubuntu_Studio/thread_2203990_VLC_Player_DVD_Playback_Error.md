---
title: "VLC Player DVD Playback Error"
date: 2014-02-06
forum: Ubuntu Studio
---

### Post by ddragon2 on 2014-02-06
Environment: Windows 7 and Ubuntu Dual Boot
Version: Ubuntu Studio 13.10
--
I don't think you need my sys specs but I list them just in case...
--
CPU: AMD FX 4100 Quad-core processor
Video: AMD Radeon HD 4250 (on-board)
Memory: 6GB DDR3
HD: 1.5TB and some other HDs via USB
DVD/CD: Combo drive
Sound: AMD HDMI on-board: Disabled
Sound: M-Audio Delta 66 PCI

I am a heavy DAW user in my Windows environment using Sonar, Sony (Vegas Pro, SoundForge, Acid, CD/DVD Architect) etc..for live recordings, then editing video/audio editing then mastering etc to produce CDs and DVDs.  But I thought I would try Ubuntu Studio just to expand my knowledge, which should be equipped just in case I run into that environment one day if someone asks me to use their equipment.  

So far, everything has been gone well...until my daughter asked me to play an encrypted DVD.

I followed the steps to below to make it happen b/c Ubuntu Studio would no run it w/o "libdvdread2".  Then, a few hours later I found out "ibdvdread4."

But, when I start VLC > Media > DVD (a radio button) > Disc Device (/dev/dvd) > Play, I get the following:

Playback failure:DVDRead could not open the disc "/dev/dvd"
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/dvd' check log for details.

So, I researched further:

 cyproject@cyproject-Aspire-M3450:~$ mount|grep ^'/dev'/dev/sda5 on / type ext4 (rw,errors=remount-ro)


cyproject@cyproject-Aspire-M3450:~$ sudo lshw -C disk
 *-disk                  
       description: ATA Disk
       product: WDC WD15EARX-22P
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 51.0
       serial: WD-WCAZAC065979
       size: 1397GiB (1500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=4096 signature=e5515bf9
  *-cdrom
       description: DVD-RAM writer
       product: DVDRAM GH70N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/sr0
       version: UGA0
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
  *-disk:0
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdb
       configuration: sectorsize=512
  *-disk:1
       description: SCSI Disk
       physical id: 0.0.1
       bus info: scsi@6:0.0.1
       logical name: /dev/sdc
       configuration: sectorsize=512
  *-disk:2
       description: SCSI Disk
       physical id: 0.0.2
       bus info: scsi@6:0.0.2
       logical name: /dev/sdd
       configuration: sectorsize=512
  *-disk:3
       description: SCSI Disk
       physical id: 0.0.3
       bus info: scsi@6:0.0.3
       logical name: /dev/sde
       configuration: sectorsize=512
  *-disk:4
       description: SCSI Disk
       physical id: 0.0.4
       bus info: scsi@6:0.0.4
       logical name: /dev/sdf
       configuration: sectorsize=512


cyproject@cyproject-Aspire-M3450:~$ ls -l /dev/{cd,dvd,scd,sr}*
ls: cannot access /dev/dvd*: No such file or directory
ls: cannot access /dev/scd*: No such file or directory
lrwxrwxrwx  1 root root      3 Feb  6 06:18 /dev/cdrom -> sr0
brw-rw----+ 1 root cdrom 11, 0 Feb  6 06:18 /dev/sr0

Please let me know what I have been doing wrong here?
If you need any further information, please let me know!

Regards,

---

### Post by ddragon2 on 2014-02-06
Please do not say "just go back to Win!" b/c my daughter does not mind listening to and/or seeing whatever I am doing for inputting wise (turning down to low), while she watches movies...  So, she sees me composing or whatever, but main volume is 90% dedicated to for a DVD she is watching.  It doesn't matter however it is but my system just cannot run any DVDs even if I am not doing anything in Ubuntu Studio.

Regards,

---

### Post by westie457 on 2014-02-06
ddragon2 welcome to UF.

Now I am not going to offer a lot of technical help mainly because most of what you are doing is way above my head.

If you have already looked at this page [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) and tried those suggestions I will not be able to help further.

Someone who knows more than me will find this and help.

Using Windows is usually suggested only if all attempts at a fix fail.

---

### Post by jejeman on 2014-02-06
Optical devices are registred as /dev/srX
Symbolic link /dev/dvd is not created by default in Ubuntu studio or any other Ubuntu.
You can eather
1. make the symbolic link
2. point VLC to actual device node

---

