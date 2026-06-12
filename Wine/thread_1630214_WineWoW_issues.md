---
title: "Wine/WoW issues"
date: 2010-11-24
forum: Wine
---

### Post by ric00015 on 2010-11-24
I am running Wow 4.0.3 on Linux Mint 9 using Wine 1.2.1 I use PlayonLinux to manage Wine versions, and I have used up to 1.3.7, which I think is the most current version. Usually, it'll run OK. But I have run across several problems.

1. Logging on: When I log on, sometimes the computer will become completely non responsive. The cursor moves, bot the sound stops, no buttons can be pushed, and keyboard shortcuts don't work. This happens only after I enter my login information and press enter. The only way around this is to reset my computer.

2. Disconnection: getting DC'd is a common problem. When I ran WoW under Windows, it happened. Now, however, when I get DC'd, instead of returning to the login screen with the disconnect error message, I stay in the game until I minimize it and kill that process.

3. Minimizing: The problem lies not with the minimizing, but with getting back into the game after I use my web browser or something. I think I fixed it by running in Windowed(maximized) mode, and just switching desktops, but I haven't tried that extensively. In any case, the first 2 problems are much more annoying.

4. FPS: Every so often, I will get a huge drop in frame rate, stay that way for a few seconds or so, and go back to normal. This is independent of being in high-lag areas like Dalaran or major population centers. I used the MaxFPS tip found on AppDB, but again I haven't tested it thoroughly yet. May just be a hardware issue (see below).

If anyone has any information on any item, it will be appreciated. I have searched for these problems already. But with one exception, I haven't found the same ones listed already. I have posted this on AppDB, and am trying to get answers through multiple channels. Yes, I realize that I'm not using Ubuntu, but since Mint is based off Ubuntu, I thought there might be help here anyway.I am new to Linux, so I am still learning. I am hoping to get WoW running at least as well in Linux as on Windows.

Comp Specs (4-5 years old)
AMD Athalon 64 3200+
2.5 GB RAM
ATI Radeon HD 4350
 Driver Packaging Version: 8.723.1-100408a-098580C-ATI (proprietary)
 2D Driver Version: 8.72.11
 OpenGL Version: 3.2.9756 Compatibility Profile Context
Kernel 2.6.32-21-generic
Linux Mint 9 32-bit (will upgrade to 10 soon)
Gnome 2.30.2

---

### Post by ric00015 on 2010-11-24
Sorry for not posting this before, but here's my lspci output:

```

00:00.0 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 Communication controller: Conexant Systems, Inc. HCF 56k Data/Fax/Voice Modem (Worldwide) (rev 08)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]
01:00.1 Audio device: ATI Technologies Inc RV710/730

```

---

