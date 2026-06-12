---
title: "I have 2 USB controllers, looking to disable one"
date: 2009-02-24
forum: Server Platforms
---

### Post by wstout on 2009-02-24
I am running Ubuntu Server 8.04.2 and it appears my USB external hard drive is working at USB 1.0 speeds. I installed a 2.0 PCI card (strangely enough this server had a usb controller but no usb)but I am getting extremely slow transfer speeds. Here is the output of lspci:

```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 02)
00:0b.0 VGA compatible controller: Cirrus Logic GD 5446 (rev 45)
00:0d.0 PCI bridge: Digital Equipment Corporation DECchip 21150 (rev 04)
00:0e.0 System peripheral: Compaq Computer Corporation Advanced System Management Controller
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
00:10.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
00:12.0 PCI bridge: IBM PCI to PCI Bridge (IBM27-82351) (rev 07)
00:14.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:14.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:14.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:14.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
01:07.0 Network controller: Compaq Computer Corporation Netelligent Integrated 10/100 TX UTP (rev 10)
01:09.0 SCSI storage controller: LSI Logic / Symbios Logic 53c875 (rev 14)
01:09.1 SCSI storage controller: LSI Logic / Symbios Logic 53c875 (rev 14)
02:00.0 Mass storage controller: Compaq Computer Corporation Smart-2/P RAID Controller (rev 03)
```

It appears to me that the card I installed has a 2.0 and 1.1 controller also, so needless to say I would prefer to have 2.0 speeds anyone have any suggestions?

---

