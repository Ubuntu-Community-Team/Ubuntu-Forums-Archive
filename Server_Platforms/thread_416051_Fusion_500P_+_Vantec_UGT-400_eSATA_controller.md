---
title: "Fusion 500P + Vantec UGT-400 eSATA controller"
date: 2007-04-20
forum: Server Platforms
---

### Post by lebel on 2007-04-20
Hi,

I'm having issues with configuring a Fusion 500P eSATA libary (5 slots for 5 drives), Vantec UGT-400 eSATA controller (Silicon Image's 3132 chipset) and Ubuntu Server 7.04.  The current kernel being used is 2.6.20-15-server.

The thing is, the machine boots, the OS sees only one drive and the others seems to be just ignored.  Is there something I need to setup or configure for it to work?  I'm including the part of the dmesg that seems to concern the controller.  Could it be related to Port Multiplier support (or lack of thereof) ?

> ```

[...]
[    5.369685] sata_sil24 0000:13:00.0: version 0.8
[    5.369980] ACPI: PCI Interrupt 0000:13:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[    5.370158] PCI: Setting latency timer of device 0000:13:00.0 to 64
[    5.370307] ata1: SATA max UDMA/100 cmd 0xf8930000 ctl 0x00000000 bmdma 0x00000000 irq 16
[    5.370395] ata2: SATA max UDMA/100 cmd 0xf8932000 ctl 0x00000000 bmdma 0x00000000 irq 16
[    5.370433] scsi1 : sata_sil24
[    5.495847] Attempting manual resume
[    5.495852] swsusp: Resume From Partition 8:5
[    5.495854] PM: Checking swsusp image.
[    5.498071] PM: Resume from disk failed.
[    5.514929] kjournald starting.  Commit interval 5 seconds
[    5.514948] EXT3-fs: mounted filesystem with ordered data mode.
[    5.814391] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.852380] ata1.00: ata_hpa_resize 1: sectors = 625142448, hpa_sectors = 625142448
[    5.852390] ata1.00: ATA-7: ST3320620AS, 3.AAK, max UDMA/133
[    5.852395] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    5.910655] ata1.00: ata_hpa_resize 1: sectors = 625142448, hpa_sectors = 625142448
[    5.910664] ata1.00: configured for UDMA/100
[    5.910682] scsi2 : sata_sil24
[    5.924518] usb 2-2: new low speed USB device using uhci_hcd and address 2
[    6.193519] usb 2-2: configuration #1 chosen from 1 choice
[    6.244520] ata2: SATA link down (SStatus 0 SControl 300)
[    6.244646] scsi 1:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
[    6.244725] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[    6.244741] sdb: Write Protect is off
[    6.244745] sdb: Mode Sense: 00 3a 00 00
[...]

```

Any tips? Hints?  Thanks!

---

### Post by powder on 2007-05-29
Hello,

I believe I am having the same problem.  I am using the SiI 3132 chip for ESATA which should recognize the SiI 3726 port multiplier.  With the proper driver installed you should be able to see up to 5 drives through the 3132 chip.  So far it's only recognizing 1 SATA link (SATALink 0).

Any help would be appreciated.  Here is more info on the port multiplier...

**SATALink SATA II Port Multiplier**
SiI3726 is a 1-to-5 Serial ATA (SATA) Port Multiplier designed to provide a high-performance link between a single SATA host port and five SATA device ports. The SiI3726 supports host and device link rates of 1.5 Gbps and 3 Gbps with auto-negotiation, giving system designers or end users the flexibility to choose 1.5 Gbps or 3 Gbps SATA hard drives.

[IMG]http://img239.imageshack.us/img239/7141/satalt1.jpg[/IMG]

---

