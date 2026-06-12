---
title: "Microsoft Office 2007 Not Working"
date: 2011-05-14
forum: Wine
---

### Post by plzdontkillme11 on 2011-05-14
Hey guys,

I've installed Microsoft Office 2007 with wine, but when I click on any of the applications, there is no response. I'm running version 1.3.18 (this is the version that WineHQ recommended) on a Toshiba Satellite l305, Ubuntu 11.04.

Results for lspci:

```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```

Thanks in advance.

---

### Post by plzdontkillme11 on 2011-05-14
Update:

Wine and winetricks both take at least 5 minutes to start up. Office Apps still won't respond at all.

I just remembered this, and forgot to mention:

I compiled Wine 1.3.18 with ./tools/wineinstall. Before it started, however, a warning showed up, telling me that binaries for another version was still present. Well, I had already spent an hour completely removing my previous wine (and getting the same error message over and over again), so I got fed up and just installed.

Could these problems stem from conflicting wine versions?

---

### Post by OrbJinzo on 2011-05-15
From what I seen on winehq alot the applications that come with office are garage or silver. I also noticed it recommended that you have a direct rendering capable card. As far as I know intel video adapters dont do this in linux all to well and no one has had the right mind to code a proper driver for it. 

With that being said you can always install office 2k3 or use libre office

---

### Post by plzdontkillme11 on 2011-05-15
Hm, the thing is, I had the office apps, except powerpoint, working before an update totally screwed up my original Unity. I'm using Unity 2d right now.

---

### Post by plzdontkillme11 on 2011-05-15
Nevermind guys, I finally found a fix that resolved both the slow boot and no response from office apps. Just type in wineboot --update in the terminal and wait for it to finish. All should work well now.

---

