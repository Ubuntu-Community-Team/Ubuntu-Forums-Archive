---
title: "SiL 3124/3132 and Port Multiplier issues"
date: 2012-07-08
forum: Server Platforms
---

### Post by MakOwner on 2012-07-08
I have some (well, three to be exact) 8 bay external eSATA enclosures.
All three are from the same manufacturer but from different time periods - two are SATA II and the latest SATA III capable enclosures.

When I set up the last enclosure, I used 12.04 LTS and I noticed issues with the boot sequence not being able to spin up the drives in time to get them online before the boot process/udevd started timeing out.
A warm reboot will (usually) get through the boot process, but a cold power up will almost always end up in a busybox shell with the boot process halted.

 I RMA'd the last enclosure and the vendor replaces the PMs and all internal wiring of the enclosure.

I have tried this with three different Silicon Image PM compatible controllers, two differrent sets of hard drives and from a couple different servers, although they were both the same model - Poweredge 850s.  

I think I have eliminated all of the hardware components in this, and that leaves the software -- The module in use for the controller is sata_sil24.   

I'm looking for some assistance in what I can do to overcome whatever the issue is that causes the errors like you see here.
Note the older enclosure show the same reset behavior during boot as the newer one, but only the newer on has the HPA message.


```

[    1.178598] ata5: SATA max UDMA/100 host m128@0xfe9ffc00 port 0xfe9f4000 irq 16
[   89.368022] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[   89.368284] ata5.15: Port Multiplier 1.1, 0x1095:0x3726 r23, 6 ports, feat 0x1/0x9
[   89.384168] ata5.00: hard resetting link
[   89.800150] ata5.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[   89.800244] ata5.01: hard resetting link
[   90.200146] ata5.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   90.200242] ata5.02: hard resetting link
[   90.600142] ata5.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   90.600230] ata5.03: hard resetting link
[   91.000144] ata5.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   91.000238] ata5.04: hard resetting link
[   91.336233] ata5.04: SATA link down (SStatus 0 SControl 320)
[   91.336340] ata5.05: hard resetting link
[   91.672218] ata5.05: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
[   91.715301] ata5.00: ATA-7: ST3750641NS, 4IST, max UDMA/133
[   91.715368] ata5.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   91.773609] ata5.00: configured for UDMA/100
[   96.772032] ata5.01: qc timeout (cmd 0x27)
[   96.788021] ata5.01: failed to read native max address (err_mask=0x5)
[   96.788089] ata5.01: HPA support seems broken, skipping HPA handling
[   96.788163] ata5.15: hard resetting link
[   98.916026] ata5.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[   98.916297] ata5.00: hard resetting link
[   99.332144] ata5.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[   99.332240] ata5.01: hard resetting link
[   99.748142] ata5.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   99.748230] ata5.02: hard resetting link
[  100.148148] ata5.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  100.148241] ata5.03: hard resetting link
[  100.548143] ata5.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  100.548233] ata5.05: hard resetting link
[  100.884214] ata5.05: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
[  100.977722] ata5.00: configured for UDMA/100
[  100.978427] ata5.01: ATA-7: ST3750641NS, 4IST, max UDMA/133
[  100.978493] ata5.01: 1465149168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[  100.979299] ata5.01: configured for UDMA/100
[  105.980020] ata5.02: qc timeout (cmd 0x27)
[  105.996019] ata5.02: failed to read native max address (err_mask=0x5)
[  105.996087] ata5.02: HPA support seems broken, skipping HPA handling
[  105.996160] ata5.15: hard resetting link
[  108.124022] ata5.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[  108.124293] ata5.00: hard resetting link
[  108.540146] ata5.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[  108.540236] ata5.01: hard resetting link
[  108.956148] ata5.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  108.956242] ata5.02: hard resetting link
[  109.372145] ata5.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  109.372240] ata5.03: hard resetting link
[  109.772148] ata5.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  109.772242] ata5.04: hard resetting link
[  110.108237] ata5.04: SATA link down (SStatus 0 SControl 320)
[  110.108346] ata5.05: hard resetting link
[  110.444214] ata5.05: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
[  110.531682] ata5.00: configured for UDMA/100
[  110.533151] ata5.01: configured for UDMA/100
[  110.533835] ata5.02: ATA-7: ST3750641NS, 4IST, max UDMA/133
[  110.533903] ata5.02: 1465149168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[  110.534707] ata5.02: configured for UDMA/100
[  115.532056] ata5.03: qc timeout (cmd 0x27)
[  115.548016] ata5.03: failed to read native max address (err_mask=0x5)
[  115.548084] ata5.03: HPA support seems broken, skipping HPA handling
[  115.548157] ata5.15: hard resetting link
[  117.676021] ata5.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[  117.676288] ata5.00: hard resetting link
[  118.092150] ata5.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[  118.092243] ata5.01: hard resetting link
[  118.508144] ata5.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  118.508240] ata5.02: hard resetting link
[  118.924150] ata5.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  118.924242] ata5.03: hard resetting link
[  119.340145] ata5.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  119.340240] ata5.05: hard resetting link
[  119.676213] ata5.05: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
[  119.769117] ata5.00: configured for UDMA/100
[  119.770593] ata5.01: configured for UDMA/100
[  119.772062] ata5.02: configured for UDMA/100
[  119.772770] ata5.03: ATA-7: ST3750641NS, 4IST, max UDMA/133
[  119.772837] ata5.03: 1465149168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[  119.773611] ata5.03: configured for UDMA/100
[  119.773713] ata5: EH complete

```

---

