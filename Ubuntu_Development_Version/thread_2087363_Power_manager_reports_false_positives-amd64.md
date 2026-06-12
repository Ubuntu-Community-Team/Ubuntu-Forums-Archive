---
title: "Power manager reports false positives-amd64"
date: 2012-11-23
forum: Ubuntu Development Version
---

### Post by ventrical on 2012-11-23
Doing  a raw power test on Acer Extensa 4420 amd64AthlonX2 it initially reported 18hrs!! of time then 1 minute later reports battery is critically low/ then/reboot/ then bring up power settings, reports critally low, then starts to increase in time.

  This battery will give me 2hrs40 minutes on Mint Julia.

Well over 1/2 hour has past and the power indicator still reports 48 minutes. I am writing this message from said PC.
```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS690 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI Device 7914
00:05.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI1)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI2)
00:13.3 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI3)
00:13.4 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB600 IDE
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS690M [Radeon X1200 Series]
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
0b:06.0 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
0b:06.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0b:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
0b:06.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0c:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
ubuntu@ubuntu:~$ 

```


note..usually this PC runs very warm but it running cool at present (fingers crossed)

---

### Post by ventrical on 2012-11-23
side-note .. This may be an hardware error due to a miscalculation on my part.

---

### Post by ventrical on 2012-11-23
Using raring-desktop-i386.iso daily on an Acer Aspire 3620, consumed 20 minutes of time with only 1% gone.

Re: live USB , no hdd.

---

### Post by ventrical on 2012-11-23
1 hour has elapsed and only 2% poer used. I tried to run a movie, it crashed but recovered itself while in live mode (no reboot), ran gedit, wrote a file, running system monitor, firefox... I am just testing to see if any of the new power management features are woking.

---

### Post by ventrical on 2012-11-23
Serious bugs with power management...calibration..

---

