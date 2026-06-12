---
title: "Understanding what I see in syslog"
date: 2012-10-08
forum: Server Platforms
---

### Post by fade2gray on 2012-10-08
I have Ubuntu 10.04.3 LTS server edition running as a VirtualBox VM on Windows Vista. The VM comprises 3 virtual HDDs, /dev/sda, /dev/sdb and /dev/sdc.

In syslog I see references to ata1 through ata7 inclusive. Can anyone explain why this is?

Thanks for any info.

---

### Post by spynappels on 2012-10-08
> **fade2gray said:**
> I have Ubuntu 10.04.3 LTS server edition running as a VirtualBox VM on Windows Vista. The VM comprises 3 virtual HDDs, /dev/sda, /dev/sdb and /dev/sdc.

In syslog I see references to ata1 through ata7 inclusive. Can anyone explain why this is?

Thanks for any info.

Could you post some of the actual syslog entries in code tags please?

---

### Post by fade2gray on 2012-10-08
Thanks for the reply.
```
Oct  8 13:39:25 f2g kernel: [    0.721063] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0xe000 irq 14
Oct  8 13:39:25 f2g kernel: [    0.721088] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0xe008 irq 15
<snip>
Oct  8 13:39:25 f2g kernel: [    1.737733] ata3: SATA max UDMA/133 abar m8192@0xf0900000 port 0xf0900100 irq 24
Oct  8 13:39:25 f2g kernel: [    1.737754] ata4: SATA max UDMA/133 abar m8192@0xf0900000 port 0xf0900180 irq 24
Oct  8 13:39:25 f2g kernel: [    1.737769] ata5: SATA max UDMA/133 abar m8192@0xf0900000 port 0xf0900200 irq 24
Oct  8 13:39:25 f2g kernel: [    1.737785] ata6: SATA max UDMA/133 abar m8192@0xf0900000 port 0xf0900280 irq 24
Oct  8 13:39:25 f2g kernel: [    1.737800] ata7: SATA max UDMA/133 abar m8192@0xf0900000 port 0xf0900300 irq 24
```
I'm trying to debug errors like...
```
Oct  2 02:16:49 f2g kernel: [31653.040168] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Oct  2 02:16:49 f2g kernel: [31653.048522] ata3.00: failed command: FLUSH CACHE
Oct  2 02:16:49 f2g kernel: [31653.050075] ata3.00: cmd e7/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Oct  2 02:16:49 f2g kernel: [31653.050075]          res 40/00:00:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
Oct  2 02:16:49 f2g kernel: [31653.067518] ata3.00: status: { DRDY }
Oct  2 02:16:49 f2g kernel: [31653.074299] ata3: hard resetting link
Oct  2 02:16:49 f2g kernel: [31653.422986] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct  2 02:16:49 f2g kernel: [31653.423284] ata3.00: configured for UDMA/133
Oct  2 02:16:49 f2g kernel: [31653.423289] ata3.00: device reported invalid CHS sector 0
Oct  2 02:16:49 f2g kernel: [31653.423301] ata3: EH complete
```

---

### Post by spynappels on 2012-10-09
I don't have a version of VirtualBox to hand to look at, but is VB telling the OS that it has disks connected to (virtual) SATA ports?

The first excerpt looks like a normal startup, where the OS checks the (virtual) hardware and finds 2 PATA and 5 SATA ports. The second excerpt looks like there is something funny going on with the virtual disk attached to ata3, which is the first virtual SATA port.

What is the base problem you are trying to fix?

---

### Post by spynappels on 2012-10-09
Just as an aside, does this match the problem you are seeing?

[https://forums.virtualbox.org/viewtopic.php?f=3&t=46722&p=210902&hilit=invalid+chs+sector#p211916](https://forums.virtualbox.org/viewtopic.php?f=3&t=46722&p=210902&hilit=invalid+chs+sector#p211916)

---

