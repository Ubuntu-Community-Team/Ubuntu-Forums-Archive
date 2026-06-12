---
title: "Mercury RACEway Bridge"
date: 2006-05-08
forum: Server Platforms
---

### Post by cilynx on 2006-05-08
Anyone know anything about this card?

```

0000:03:04.0 RACEway bridge: Mercury Computer Systems Raceway Bridge (rev 01) (prog-if 01 [Endpoint mode])
        Subsystem: Mercury Computer Systems: Unknown device 0000
        Flags: bus master, slow devsel, latency 32, IRQ 10
        Memory at d4000000 (32-bit, prefetchable) [size=64M]
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at fea00000 (32-bit, non-prefetchable) [size=1M]
        Expansion ROM at d2400000 [disabled] [size=256K]

```

I'm stripping an old server that came my way and it's got a pair of these guys with what looks like a short SCSI cable connecting them together as well as an old Seagate SCSI drive hanging off a cable coming off of a second port on one of them.  They have 3 ribbon hookups on the top and one on the "face" of the card.  Also, these are really long cards that rely on the plastic support rail on the front of the cabinate.

I'm guessing these are glorified SCSI controllers, but I can't find much of any info about them or RACEway in general, let alone drivers.  It looks like a reasanably high-band protocol from the mid 90's, but that's about all I can figure.  

Anyone ever seen one of these doing anything useful?

Thanks --

---

