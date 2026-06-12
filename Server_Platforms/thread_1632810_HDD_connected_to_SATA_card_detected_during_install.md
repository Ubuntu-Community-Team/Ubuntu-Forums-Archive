---
title: "HDD connected to SATA card detected during install but not after install"
date: 2010-11-28
forum: Server Platforms
---

### Post by t_anjan on 2010-11-28
Hi!

My hard disk configuration is as below:
1 x IDE hard disk connected to the motherboard directly (ASRock K7VM-3)
2 x SATA hard disks connected to a PCI SATA card. Not sure about the brand or model of this card.

The computer being quite old, I chose to install the Ubuntu minimal version (10.04). I wanted to install just the command line version. 

During the install, the installer showed me all three hard disks. I chose to install on the IDE hard disk.

But after installation, Ubuntu doesn't seem to detect the PCI SATA card and the SATA hard disks.

lspci -nn shows the following:
```
00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge [1106:3205]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237/VX700 PCI Bridge [1106:b198]
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 82)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8235 ISA Bridge [1106:3177]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] [1106:7205] (rev 01)

```

sudo fdisk -l shows the following:
```
Disk /dev/sda: 10.2 GB, 10204766208 bytes
255 heads, 63 sectors/track, 1240 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cef7d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1182     9490432   83  Linux
/dev/sda2            1182        1241      473089    5  Extended
/dev/sda5            1182        1241      473088   82  Linux swap / Solaris
```

I am pretty sure this has something to do with the Minimal version of Ubuntu not installing / loading a certain module which "sees" the sata hard disks. I would appreciate it if someone can point me in the right direction.

Thanks.
Anjan

---

### Post by t_anjan on 2010-12-01
Never mind. The PCI card is dead.

Figures.

---

