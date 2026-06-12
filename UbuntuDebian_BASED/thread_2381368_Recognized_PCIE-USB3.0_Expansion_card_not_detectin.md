---
title: "Recognized PCIE-USB3.0 Expansion card not detecting any USB deiv"
date: 2017-12-30
forum: Ubuntu/Debian BASED
---

### Post by ckinren on 2017-12-30
Hi, experiencing the exact same problem.
My pcie card is an Tecknet EU303B, motherboard is an MSI FM2-A55M-E33 and OS is elementary 0.4 with kernel 4.4.0-104

From the lspci and lsusb outputs (see below) it seems that the card is seen by the system, host controller and root hub are there but something is stopping them detecting any usb device connected into any of the 4 ports.
Additional power has been supplied from the psu to the card (seen this mentioned a few times as possible cause).

I did read somewhere that the Via chipset does not work  if IOMMU is enabled, pretty sure it related to the VL805 chip.
It mentioned disabling it in the motherboard bios settings - unfortunately I can't say whether this works or not as although IOMMU seems present and enabled on my system (see lspci below) I can found nowhere in my bios settings to be able to disable it.

I failed to bookmark the site/post and I haven't found it again.

There are sites with posts indicating that IOMMU can be disabled in GRUB, but I'm not sure I have the technical savvy to be able to accomplish this without screwing my system up, especially as it might not be a solution anyway.

If anyone has any guidance they can provide it would be much appreciated.

```
  craig@craig-MS-7721:~$lspci
00:00.0Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models10h-1fh) Processor Root Complex
00:00.2IOMMU: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh)I/O Memory Management Unit
00:01.0VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI]Trinity [Radeon HD 7560D]
00:01.1Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMIAudio Controller
00:04.0PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models10h-1fh) Processor Root Port
00:05.0PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models10h-1fh) Processor Root Port
00:11.0SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATAController [AHCI mode] (rev 40)
00:12.0USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCIController (rev 11)
00:12.2USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCIController (rev 11)
00:13.0USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCIController (rev 11)
00:13.2USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCIController (rev 11)
00:14.0SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev14)
00:14.2Audio device: Advanced Micro Devices, Inc. [AMD] FCH AzaliaController (rev 01)
00:14.3ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev11)
00:14.4PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev40)
00:14.5USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCIController (rev 11)
00:16.0USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCIController (rev 11)
00:16.2USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCIController (rev 11)
00:18.0Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models10h-1fh) Processor Function 0
00:18.1Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models10h-1fh) Processor Function 1
00:18.2Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models10h-1fh) Processor Function 2
00:18.3Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models10h-1fh) Processor Function 3
00:18.4Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models10h-1fh) Processor Function 4
00:18.5Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models10h-1fh) Processor Function 5
01:00.0Ethernet controller: Realtek Semiconductor Co., Ltd.RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
02:00.0USB controller: VIA Technologies, Inc. VL805 USB 3.0 Host Controller(rev 01)
```

```
craig@craig-MS-7721:~$lsusb
Bus003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus001 Device 002: ID 048d:1336 Integrated Technology Express, Inc.SD/MMC Cardreader
Bus001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus004 Device 002: ID 046a:0101 Cherry GmbH 
Bus004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by howefield on 2017-12-30
Thread moved to the "*Ubuntu/Debian BASED*" forum and code tags added.

---

