---
title: "How to enable  LTO2 Compression?"
date: 2011-10-16
forum: Server Platforms
---

### Post by bobbennett on 2011-10-16
Hello,

I have an ADIC Fastor2 tape library with an HP LTO2 tape drive.  It works well except I can't seem to enable compression.  

I have tried:
* Blowing away and letting Ubuntu recreate /dev/st* files.
* Setting compression=1 in /etc/stinit.def.
* Turning on compression with mt.
* A few other odds & ends.

Do I need a driver for this?  Any suggestions?

/proc/scsi/scsi contains (among other things):
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: ADIC     Model: FastStor 2       Rev: G12r
  Type:   Medium Changer                   ANSI  SCSI revision: 02
Host: scsi2 Channel: 00 Id: 05 Lun: 00
  Vendor: HP       Model: Ultrium 2-SCSI   Rev: F67A
  Type:   Sequential-Access                ANSI  SCSI revision: 03

However, /proc/scsi/device_info only shows LTO3 type devices:
'HP' 'Ultrium 3-SCSI' 0x1
'IBM' 'ULTRIUM-TD3' 0x1



Thank you.

bob

---

