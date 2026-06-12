---
title: "No available Sound Outputs with latest packages"
date: 2016-09-29
forum: Ubuntu Development Version
---

### Post by darran-kelinske on 2016-09-29
I am running a Sound Blaster Live. After updating to the latest packages I now don't have any sound outputs available.

Thank you for the help! I can see it listed in lspci

```
daz@iloveyou:/media/development/source/emeritus/chat-app-android$ sudo lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RX780/RX790 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RX780/RD790 PCI to PCI bridge (external gfx0 port A)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD790 PCI to PCI bridge (PCI express gpp port A)
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RX780/RD790 PCI to PCI bridge (PCI express gpp port D)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Barts XT [Radeon HD 6870]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Barts HDMI Audio [Radeon HD 6800 Series]
02:00.0 Network controller: Qualcomm Atheros AR93xx Wireless Network Adapter (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)
04:07.0 Multimedia audio controller: Creative Labs EMU10k1 [Sound Blaster Live! Series] (rev 05)
04:07.1 Input device controller: Creative Labs SB Live! Game Port (rev 05)

```

[ATTACH=CONFIG]271429[/ATTACH]

---

### Post by fthx on 2016-09-29
From CKT ppa ? :

linux (4.8.0-19.21) yakkety; urgency=low

 * linux-image-extra-4.8.0-17-generic does not provide many sound card modules
    (LP: [#1628523]("https://launchpad.net/bugs/1628523"))
    - [Config] CONFIG_ZONE_DMA=y for generic

---

### Post by darran-kelinske on 2016-09-29
Good find. Thank you!

---

