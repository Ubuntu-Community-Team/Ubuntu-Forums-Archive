---
title: "No sound options after update to 20.04"
date: 2020-09-29
forum: Ubuntu/Debian BASED
---

### Post by leroti on 2020-09-29
Hey,

so I recently updated my ubuntu from the old LTS to 20.04 running KDE Neon. During the update root ran out of space and I needed to fix a few things. Now It's running but ever since, there's no sound options. I do have sound but I can't change the volume level. I tried to reinstall pulseaudio already but that didn't change anything.

This is the output of lspci:

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09) 
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09) 
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) 
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04) 
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) 
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05) 
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) 
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5) 
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5) 
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) 
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset LPC Controller (rev 05) 
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port Mobile SATA AHCI Controller (rev 05) 
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05) 
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series] 
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06) 
0d:00.0 Network controller: Broadcom Inc. and subsidiaries BCM4313 802.11bgn Wireless Network Adapter (rev 01) 
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
```

I don't really know what I could do, since having audio seems to indicate that the soundcard driver shouldn't be the problem.. ?

Hoping somebody can help me..
Thanks !

---

### Post by QIII on 2020-09-29
Moved to Ubuntu/Debian BASED

---

### Post by exploder on 2020-09-30
There is a solution on the Neon forum for this. I tried it briefly and ran into the same issue.

---

