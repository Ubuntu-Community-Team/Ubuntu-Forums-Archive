---
title: "Does a Sigmatel STAC9200 do 'JACK'?  Also, live input monitoring"
date: 2012-04-12
forum: Ubuntu Studio
---

### Post by K-Ghidorah on 2012-04-12
Greetings!

I'm curious if anyone here has ever gotten JACK to work on a Dell Latitude D620.  I've tried many, many times but each attempt has met with failure.  Currently running Ubuntu 11.10, but this hasn't ever worked from Ubuntu (Lucid, Maverick, or Natty, Ubuntu Studio and otherwise), Linux Mint 9 XFCE, AVLinux 5.1, Linux Mints 10, 11, or 12.

Here's the output from lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```The soundcard is a Sigmatel STAC9200.  I've never been successfully able to monitor my input when recording through the mic jack (no actual line-in).

You can understand why I'm rather frustrated.  Help would definitely be appreciated.

---

### Post by sgx on 2012-04-14
[http://answer.recipester.org/question/67630/how-to-solve-the-problem-that-Sigmatel-STAC9200-has-no-sound](http://answer.recipester.org/question/67630/how-to-solve-the-problem-that-Sigmatel-STAC9200-has-no-sound)

This person has it working, and some steps to take.
Hope it helps.
Cheers

also the ideas in the rakarrack topic above, regarding
names to call devices in qjackctl, might help.

---

### Post by K-Ghidorah on 2012-05-09
I have no problem hearing sound from playback, but I will try those things that you mentioned, and look at that rakarrack topic you mentioned for some ideas and let you know how that works out.

---

