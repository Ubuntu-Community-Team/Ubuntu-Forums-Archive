---
title: "Mysterious Harddrive Errors"
date: 2010-07-14
forum: Server Platforms
---

### Post by gencha on 2010-07-14
When I restarted one of my servers today and actually worked directly on the system (not through SSH as usual), some weird error messages kept appearing in the console. So I checked the syslog and found several instances of the following lines:

```

Jul 14 21:44:07 dump kernel: [ 2100.700647] ata6: exception Emask 0x10 SAct 0x0 SErr 0x1810000 action 0xa frozen
Jul 14 21:44:07 dump kernel: [ 2100.700694] ata6: irq_stat 0x00400000, PHY RDY changed
Jul 14 21:44:07 dump kernel: [ 2100.700720] ata6: SError: { PHYRdyChg LinkSeq TrStaTrns }
Jul 14 21:44:07 dump kernel: [ 2100.700750] ata6: hard resetting link
Jul 14 21:44:08 dump kernel: [ 2101.441527] ata6: SATA link down (SStatus 10 SControl 310)
Jul 14 21:44:08 dump kernel: [ 2101.441538] ata6: failed to recover some devices, retrying in 5 secs
Jul 14 21:44:13 dump kernel: [ 2106.444115] ata6: hard resetting link
Jul 14 21:44:14 dump kernel: [ 2107.971853] ata6: SATA link down (SStatus 10 SControl 310)
Jul 14 21:44:14 dump kernel: [ 2107.971864] ata6: failed to recover some devices, retrying in 5 secs
Jul 14 21:44:19 dump kernel: [ 2112.974439] ata6: hard resetting link
Jul 14 21:44:22 dump kernel: [ 2115.281020] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jul 14 21:44:22 dump kernel: [ 2115.315889] ata6.00: configured for UDMA/33
Jul 14 21:44:22 dump kernel: [ 2115.315902] ata6: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x9 t4
Jul 14 21:44:22 dump kernel: [ 2115.315970] ata6: irq_stat 0x00000040, connection status changed
Jul 14 21:44:22 dump kernel: [ 2115.331012] ata6.00: configured for UDMA/33
Jul 14 21:44:22 dump kernel: [ 2115.331018] ata6: EH complete
Jul 14 21:44:22 dump kernel: [ 2115.330923] sd 5:0:0:0: [sde] 2930277168 512-byte hardware sectors (1500302 MB)
Jul 14 21:44:22 dump kernel: [ 2115.330937] sd 5:0:0:0: [sde] Write Protect is off
Jul 14 21:44:22 dump kernel: [ 2115.330939] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
Jul 14 21:44:22 dump kernel: [ 2115.330953] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 14 21:44:22 dump kernel: [ 2115.330969] sd 5:0:0:0: [sde] 2930277168 512-byte hardware sectors (1500302 MB)
Jul 14 21:44:22 dump kernel: [ 2115.330976] sd 5:0:0:0: [sde] Write Protect is off
Jul 14 21:44:22 dump kernel: [ 2115.330978] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
Jul 14 21:44:22 dump kernel: [ 2115.330990] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

I don't have the slightest clue what these messages are trying to tell me. But given that some of them appear directly in the console, I figure it's kind of important.

If someone could shed some light on this, I'd really appreciate it.

---

### Post by cariboo on 2010-07-14
Those are hard drive errors you are seeing, I used to see the same thing when using fake raid. It might be a good idea to check the health of your hard drives.

---

### Post by gencha on 2010-07-14
I'm using md softraid on this server. As a matter of fact, a while after I posted, two of the drives in the server simply shut off. But I don't know if sde was one of them.
But I did check the health through mdadm and smartctl and concluded that all drives should be fine. I'm currently rebuilding the RAID.

But the error messages generally confused me. First of all, the first part mentions ata6, the second part sd 5:0:0:0:. So I wasn't even sure if ata6 refers to sde. Second of all, what part of the system is actually producing the messages? And above all, what is their actual meaning?
For example, the first 3 lines are the ones that were also printed to the console. They could hardly be any more cryptic.

---

