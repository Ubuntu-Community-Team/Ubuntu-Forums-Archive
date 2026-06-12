---
title: "Bug:  ATA Pass-Through BROKEN, bus-trace attached ."
date: 2011-03-31
forum: Security
---

### Post by mfirth on 2011-03-31
Bug:  Low 28 bits of LBA address to drive after DMA completion  (read/write), following the interrupt to the kernel, status is read from  the drive with the updated LBA address.  The 28 lower bits are then  transposed into the NEXT drive commands upper 28bits.

Confirmed:  smartmon/sgtools using a Finisar protocol analyzer.

When: Only occurs when using systems whos BIOS is set into Legacy (or  ATA/IDE) modes.  (**Does NOT occur when using AHCI bios mode**).

See attached image to see what occured when running SG tools to read the  SMART log (command 0x2F)... It becomes very obvious that the ATA  Pass-Through driver's actual data becomes over-written with the previous  commands LBA address.

Security Issue:  Correct combination/sequence of commands can allow for sector accesses to the drive which appear to the kernel to be "valid/legal" sectors, but malicious software could use this to actually compromise restricted areas of the hard-drive.

---

