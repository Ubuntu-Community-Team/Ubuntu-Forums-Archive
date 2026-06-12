---
title: "Replaced DVDRW drive not reading disks"
date: 2010-02-25
forum: Server Platforms
---

### Post by sergiom99 on 2010-02-25
Hey there,
I just replaced a DVD-RAM drive in one HP server

The drive is recognized by the OS:

```
# lshw -class disk
  *-cdrom UNCLAIMED
       description: SCSI CD-ROM
       product: DVDRAM GSA-T50L
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       version: SC04
       capabilities: removable
       configuration: ansiversion=5

```


But no CDROM, DVDROM or DVD+RW can be mounted or written:

```
# dvd+rw-mediainfo /dev/dvdrw
INQUIRY:                [HL-DT-ST][DVDRAM GSA-T50L ][SC04]
GET [CURRENT] CONFIGURATION:
:-( no media mounted, exiting...
# mount /dev/dvdrw /mnt/dvd/
mount: No medium found
```

Needless to say, I could read/write/mount the old drive.

Is there anything I should do when replacing a drive?
Didnt think so, but this is going nowhere.

Thanks a lot for your comments!

---

### Post by sergiom99 on 2010-02-26
* bump *

---

### Post by joberly on 2010-02-26
Does your BIOS identify the drive properly? Also, see this page for some information. 

[https://bugs.launchpad.net/ubuntu/+source/dvd+rw-tools/+bug/307477]("https://bugs.launchpad.net/ubuntu/+source/dvd+rw-tools/+bug/307477")

---

### Post by sergiom99 on 2010-02-26
Yes, its detected in the BIOS (thus in the OS)

---

