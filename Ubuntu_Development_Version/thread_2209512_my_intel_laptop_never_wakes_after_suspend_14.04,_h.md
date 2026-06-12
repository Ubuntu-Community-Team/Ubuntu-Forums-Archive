---
title: "my intel laptop never wakes after suspend 14.04, how can I help?"
date: 2014-03-06
forum: Ubuntu Development Version
---

### Post by timrichardson on 2014-03-06
Upgraded to 14.04 a week ago on an intel-based toshiba. The screen never wakes up after resume. I've reported a bug but there is no reaction.
How can I help to make some progress? I updated to the beta release to provide feedback, something is badly broken, and I want to help, but what do I do?

---

### Post by ventrical on 2014-03-06
> **timrichardson said:**
> Upgraded to 14.04 a week ago on an intel-based toshiba. The screen never wakes up after resume. I've reported a bug but there is no reaction.
How can I help to make some progress? I updated to the beta release to provide feedback, something is badly broken, and I want to help, but what do I do?


What year is that machine ??

 I have the Satalite A105 Centrino Duo laptop. I'll check that out.

---

### Post by ventrical on 2014-03-06
Works fine on my Intel based Toshiba Satalite A-105.


```

ventrical@ventrical-Satellite-A105:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
ventrical@ventrical-Satellite-A105:~$ 

```

---

### Post by timrichardson on 2014-03-09
The main user on this machine (my daughter) was not in the sudo group. I added her, and on the next login the automatic bug reporting kicked in, with a long list of reports due to the resume problems (which cause kernel panics according to the data).
So I feel better now; bug reports have been submitted with copious logs of data. 
The problem is still happening with the latest kernel, but at least the problem is visible now. 

So that's a tip if doing beta testing: make sure the user belongs to the sudo group.

---

### Post by timrichardson on 2014-03-09
It's 2008 from memory. It's been running ubuntu since then, there may have been problems from time to time but not for many releases, so this is a bit of a surprise. The installation was an upgrade from 13.10, not a clean install.

---

