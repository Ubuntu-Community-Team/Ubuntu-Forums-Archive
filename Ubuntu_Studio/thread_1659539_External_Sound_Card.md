---
title: "External Sound Card?"
date: 2011-01-04
forum: Ubuntu Studio
---

### Post by CosmicFlux on 2011-01-04
Hi,

I'm running Ubuntu 10.10 and use it, along with Windows 7, for sound and music production. The integrated sound capabilities of my laptop aren't that great - I get clicking noises when playing through my MIDI controller unless I increase the buffer size to an unmanageable level, leaving me with major latency issues. 

Is there an external sound card which would act as an upgrade, or are they more suited for home theatre-type stuff? I basically want to override the internal card capabilities and use something higher spec for the music production. 

Is this possible?

Cosmic

---

### Post by AutoStatic on 2011-01-04
Hello Cosmic,

That's possible. How many inputs/outputs do you need? Budget? What kind of notebook? Could you post the outcome of the terminal command **lspci** ?

Best,

Jeremy

---

### Post by CosmicFlux on 2011-01-04
Budget isn't an issue, I'm not sure about I/O. My MIDI controller is USB, as is my piano. A couple for guitar I guess.

My notebook is a Packard Bell EasyNote TM80

Here is the output:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
```

Cosmic

---

### Post by AutoStatic on 2011-01-05
Thanks! So no FireWire and no brand new USB controller that might cause issues. But how many IO do you need at least? Most USB soundcards are still USB1.1 which means they only have 2 inputs and 2 outputs you can use at once. If you need more you'll need a supported USB2 soundcard.
One of the best USB1.1 options is still the Cakewalk by Roland UA-25EX (the successor of the Edirol UA-25) I think. A cheaper option would be a M-Audio Fast Track.

---

