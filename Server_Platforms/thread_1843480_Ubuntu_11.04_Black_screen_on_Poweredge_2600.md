---
title: "Ubuntu 11.04 Black screen on Poweredge 2600"
date: 2011-09-13
forum: Server Platforms
---

### Post by sentinelace on 2011-09-13
I have an ATI onboard old graphics card and I get a black screen.  I can ssh into the box just fine.  I have tried setting the nomodeset with no luck.  Is this a driver issue?  How do I get the ATI drivers installed?

---

### Post by ajgreeny on 2011-09-13
> **sentinelace said:**
> I have an ATI onboard old graphics card and I get a black screen.  I can ssh into the box just fine.  I have tried setting the nomodeset with no luck.  Is this a driver issue?  How do I get the ATI drivers installed?
If it is an old card from ATI, you are probably stuck with the open source driver that you already have running.  Can you show the output from ```
lspci
``` in terminal please to show exactly what the card is.

---

### Post by sentinelace on 2011-09-13
```
00:00.0 Host bridge: Intel Corporation E7500 Memory Controller Hub (rev 03)
00:02.0 PCI bridge: Intel Corporation E7500/E7501 Hub Interface B PCI-to-PCI Bridge (rev 03)
00:03.0 PCI bridge: Intel Corporation E7500/E7501 Hub Interface C PCI-to-PCI Bridge (rev 03)
00:04.0 PCI bridge: Intel Corporation E7500/E7501 Hub Interface D PCI-to-PCI Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CA LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CA Ultra ATA Storage Controller (rev 02)
01:1c.0 PIC: Intel Corporation 82870P2 P64H2 I/OxAPIC (rev 03)
01:1d.0 PCI bridge: Intel Corporation 82870P2 P64H2 Hub PCI Bridge (rev 03)
01:1e.0 PIC: Intel Corporation 82870P2 P64H2 I/OxAPIC (rev 03)
01:1f.0 PCI bridge: Intel Corporation 82870P2 P64H2 Hub PCI Bridge (rev 03)
03:01.0 Ethernet controller: Intel Corporation 82544GC Gigabit Ethernet Controller (LOM) (rev 02)
04:1c.0 PIC: Intel Corporation 82870P2 P64H2 I/OxAPIC (rev 03)
04:1d.0 PCI bridge: Intel Corporation 82870P2 P64H2 Hub PCI Bridge (rev 03)
04:1e.0 PIC: Intel Corporation 82870P2 P64H2 I/OxAPIC (rev 03)
04:1f.0 PCI bridge: Intel Corporation 82870P2 P64H2 Hub PCI Bridge (rev 03)
07:1c.0 PIC: Intel Corporation 82870P2 P64H2 I/OxAPIC (rev 03)
07:1d.0 PCI bridge: Intel Corporation 82870P2 P64H2 Hub PCI Bridge (rev 03)
07:1e.0 PIC: Intel Corporation 82870P2 P64H2 I/OxAPIC (rev 03)
07:1f.0 PCI bridge: Intel Corporation 82870P2 P64H2 Hub PCI Bridge (rev 03)
08:08.0 PCI bridge: Intel Corporation 80303 I/O Processor PCI-to-PCI Bridge (rev 01)
09:0d.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 07)
09:0d.1 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 07)
0b:00.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
0b:04.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
```

---

### Post by ajgreeny on 2011-09-14
Yes, you are not able to use an proprietary ATI driver with that card, only the open source one, so what you have is as good as it is going to get.  Can you login to the classic desktop from the login screen, it is a bit more tolerant of graphic card problems than unity, so is worth trying.

---

### Post by sentinelace on 2011-09-14
I cannot get that far.  All I can do is SSH into the box.  All black screen at the box itself.

---

### Post by sentinelace on 2011-10-17
bump still need some help on this

---

### Post by sentinelace on 2011-11-19
Still a bump, I would like to have access other than ssh.  Anyone?

---

