---
title: "Error message: ata5: failed to resume link (SControl FFFFFFFF)"
date: 2010-12-15
forum: Server Platforms
---

### Post by csudess on 2010-12-15
I have a HP Proliant Dl380G3 server and i put into a sata II controller card in a pci -x port! Ive talked about this card  MV88SX6041 4-port SATA II PCI-X and i take one 650gb winchester to one port. But after i copy some files to the winchester i got this error messsage in the kern.log file:

[27907.329615] Uhhuh. NMI received for unknown reason a1 on CPU 0.
 [27907.329615] You have some hardware problem, likely on the PCI bus.
 [27907.329615] Dazed and confused, but trying to continue
 cpqphp: power fault interrupt
 cpqphp: power fault bit 1 set
 ata5: Unable to stop eDMA
 ata5.00: exception Emask 0x52 SAct 0x1 SErr 0xffffffff action 0xe frozen
 ata5: SError: { RecovData RecovComm UnrecovData Persist Proto HostInt  PHYRdyChg PHYInt CommWake 10B8B Dispar BadCRC Handshk LinkSeq
 ata5.00: failed command: WRITE FPDMA QUEUED
 ata5.00: cmd 61/10:00:cf:1d:3c/00:00:25:00:00/40 tag 0 ncq 8192 out
         res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x56 (ATA bus error)
 ata5.00: status: { DRD
 [36297.052005] ata5: Unable to stop eDMA
 [36297.082200] ata5.00: exception Emask 0x52 SAct 0x1 SErr 0xffffffff action 0xe frozen
 [36297.082617] ata5: SError: { RecovData RecovComm UnrecovData Persist  Proto HostInt PHYRdyChg PHYInt CommWake 10B8B Dispar BadCRC Handshk  LinkSeq
 [36297.083244] ata5.00: failed command: WRITE FPDMA QUEUED
 [36297.083484] ata5.00: cmd 61/10:00:cf:1d:3c/00:00:25:00:00/40 tag 0 ncq 8192 out
 [36297.083486]          res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x56 (ATA bus error)
 [36297.084183] ata5.00: status: { DRDY }
 [36297.084379] ata5: hard resetting link


I using ubuntu 10.04 server LTS! Anybody have an idea to slove my problem?!

Thank u afurther to ur answer!

---

### Post by doublemeat on 2011-05-17
Is it causing problems?

I am getting this error too when resuming from sleep. But it seems to have no effect on the system, or it's ability to sleep again. I always get the error message twice (and it takes pretty long to wake up from sleep).

...So, maybe whatever it is trying and failing to do, it succeeds on the third try?

I'm running 10.04 upgraded to 10.10, natively on a Macbook Pro 6,2.

---

