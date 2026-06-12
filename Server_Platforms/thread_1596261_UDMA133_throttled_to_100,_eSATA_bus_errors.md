---
title: "UDMA/133 throttled to 100, eSATA bus errors"
date: 2010-10-14
forum: Server Platforms
---

### Post by ElllisD on 2010-10-14
I imagine this is due to there being 5x 3Gbps devices trying to talk on 1 eSATA cable.

Rather than post 169 lines of what happened in a second on my sata bus, I've hosted the relevant syslog content [here]("http://screenshot.nocturnal.fea.st/sata%20bus%20error.txt") should a closer inspection be desired. 

The device is a 3rd Generation Drobo-S with 5x SATAII 2TB in RAID5 providing 4x 2.2TB volumes via eSATA to a Dell R210 server on a SAN.

3 Drobo volumes are LVM, the 4th is a hotspare for software RAID on internal drives.

Only the internal drives are S.M.A.R.T. aware, and they're fine.

These errors are the only output printing to screen during boot, and there's no apparent effect on normal functioning aside from a boot delay sometimes up to 6 minutes- but it's usually just under 2.

Highlights of the linked-to syslog errors are (in reverse chronological order):

ata6.03: SATA link up 3.0 Gbps (SStatus 123 SControl 310)
ata6.03: configured for UDMA/100
ata6.00: hard resetting link
ata6.03: SError: { PHYRdyChg DevExch }
ata6.03: exception Emask 0x10 SAct 0x0 SErr 0x4010000 action 0xf
ata6.02: error: { ABRT }
ata6.02: status: { DRDY ERR }
ata6.02: cmd ef/05:fe:00:00:00/00:00:00:00:00/40 tag 0
         res 41/04:fe:58:0a:00/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
ata6.02: failed command: SET FEATURES
ata6.03: limiting speed to UDMA/100:PIO4
ata6.03: configured for UDMA/133

---

