---
title: "Sound card recognised but not installed"
date: 2012-01-01
forum: Ubuntu Studio
---

### Post by Lozzy_uk on 2012-01-01
Hi,

I'm really quite new to the whole Linux scene, but enjoying it so far, mostly :)

Now to my problem, multiple hardware which work perfectly under Ubuntu 11.10, fail to work in Ubuntu Studio. One is the soundcard.

If I **lspci** I get:
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
[COLOR=DarkRed]00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)[/COLOR]
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
05:00.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)

and if I **aplay -l** I get

[COLOR=DarkRed]aplay: device_list:240: no soundcards found...[/COLOR]

Any ideas where to go from here??
Thanks

---

### Post by Lozzy_uk on 2012-01-02
It turns out I had an incomplete installation somehow.

Trying various things eventually reported a missing linux-generic-pae which I then installed, and hey presto... working mouse and soundcard now. God only knows how that happened...

*aplay -l* now reports

[COLOR=DarkRed]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/COLOR]

---

