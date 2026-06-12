---
title: "The ever present ata DRDY err."
date: 2010-04-03
forum: Testimonials &amp; Experiences
---

### Post by deadite66 on 2010-04-03
**general rant i don't expect it so be fixed just wanted to whine.**

/ranton
i see this problem time and time again on various hardware and different version of ubuntu, i have a brand new machine and can't install 9.10 or 10.04 on it due to this perennial ubuntu bug.

really wonder what the devs are up to if they keep hitting the same wall time and time again.
Windows 7 works perfectly and so does fedora 12 what is wrong with the debian/ubuntu kernel that we keep seeing this?
/rantoff

> [  776.594450] ata7.00: status: { DRDY }
[  776.594454] ata7: hard resetting link
[  777.123108] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  777.125321] ata7.00: configured for UDMA/33
[  777.125328] ata7: EH complete
[  777.151827] ata7.00: exception Emask 0x10 SAct 0x1 SErr 0x280100 action 0x6 frozen
[  777.151830] ata7.00: irq_stat 0x08000000, interface fatal error
[  777.151833] ata7: SError: { UnrecovData 10B8B BadCRC }
[  777.151836] ata7.00: failed command: READ FPDMA QUEUED
[  777.151841] ata7.00: cmd 60/08:00:bf:28:54/00:00:02:00:00/40 tag 0 ncq 4096 in
[  777.151842]          res 40/00:00:bf:28:54/00:00:02:00:00/40 Emask 0x10 (ATA bus error)
[  777.151844] ata7.00: status: { DRDY }

---

