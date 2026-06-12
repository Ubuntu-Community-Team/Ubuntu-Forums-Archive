---
title: "Game graphics issues"
date: 2010-07-20
forum: Wine
---

### Post by AClockWorkLemon on 2010-07-20
Hiya!

I'm running Ubuntu 10.04 LTS, with the latest Wine version. Recently i tried installing Dawn of War: Dark Crusade on my linux Using WINE, and it installed without a hitch, however when i opend the game, the sound was working, but the graphics consisted of my gnome panel and awn, with a black box taking up the rest of the screen. Thinking it was an issue with the game, i uninstalled.

Now i'm having the same issue with Myst 4 Revelation.

Any help would be nice, as i would like to play both games

---

### Post by asdfoo on 2010-07-20
> **AClockWorkLemon said:**
> Hiya!

I'm running Ubuntu 10.04 LTS, with the latest Wine version. Recently i tried installing Dawn of War: Dark Crusade on my linux Using Wine, and it installed without a hitch, however when i opend the game, the sound was working, but the graphics consisted of my gnome panel and awn, with a black box taking up the rest of the screen. Thinking it was an issue with the game, i uninstalled.

Now i'm having the same issue with Myst 4 Revelation.

Any help would be nice, as i would like to play both games

which video card and drivers do you have?
If you have nvidia or ati, you will get better results installing the proprietary drivers, nvidia's or fglrx respectively.

If you have an intel card, you may need to look into using ubuntu edgers.

In addition, you should be using Wine 1.2.  open a terminal and type 'wine --version'

---

### Post by AClockWorkLemon on 2010-07-20
I have installed WINE from the software center:
```
*****@Ubuntu:~$wine --version
wine-1.1.42
```How do i upgrade to 1.2.

I'm not sure what graphics card i am using (i installd ubuntu on a school laptop, however i think it is a nvida geforce). When i opened System > Administration > Hardware Drivers, it said no propitiatory drivers were installed, however both fields in the dialog were blank (see screenshot attached)

---

### Post by asdfoo on 2010-07-20
some people use a tool called envy to install correct drivers, if you want to inspect your hardware use the lspci command at a terminal and see if you can recognise anything that says nvidia

This question is not really related to Wine, so you could probably get a better response in a different subforum.

As for updating to 1.2, visit [http://winehq.org](http://winehq.org) and follow the instructions for Ubuntu under the download section.

---

### Post by AClockWorkLemon on 2010-07-21
I take it back, it is not nVidea graphics

lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
02:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
02:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
02:01.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5761e Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

```

Thanks for the other mentions (envy, etc), i will look into them. Also, what subforum SHOULD i bring up this discussion?

Thanks again,
ACWL

---

