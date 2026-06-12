---
title: "RME sound card won't work"
date: 2011-03-24
forum: Ubuntu Studio
---

### Post by Mike1962 on 2011-03-24
Hi,
I have a problem. my rme multiface won't work and I've not got a clue where to start.
It's fine in windows but won't connect in 10.10
I have it connected through a pcmci adapter as it was originally bought for a laptop.

If it's of any consiquence whilst booting up the following appears
pci=assign usses

Many thanks

Mike

---

### Post by iandunham on 2011-03-24
While the card is in the slot, try hdsploader in the terminal. This solves the problem of it not showing up sometimes.

---

### Post by Mike1962 on 2011-03-25
Thanks, tried it and this is what came up:

hdsploader - firmware loader for RME Hammerfall DSP cards
Looking for HDSP + Multiface or Digiface cards :
Card 0 : HDA Intel at 0xddbf8000 irq 45


M

---

### Post by Pablo_F on 2011-03-26
What is the terminal output of *lspci*?

---

### Post by Mike1962 on 2011-04-01
> **Pablo_F said:**
> What is the terminal output of *lspci*?
does this make sence?

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:01.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
01:01.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
01:02.0 USB Controller: NEC Corporation USB (rev 41)
01:02.1 USB Controller: NEC Corporation USB (rev 41)
01:02.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
01:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:04.0 Mass storage controller: Integrated Technology Express, Inc. ITE 8211F Single Channel UDMA 133 (rev 11)
04:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
07:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] (rev a1)

---

### Post by Mike1962 on 2011-04-01
I just took a photo of the screen that comes up. Here's what it says:
yenta_cardbus 0000:01:01:1 no bus accociated! (try 'pci+assign usses')

---

### Post by Pablo_F on 2011-04-01
Hi, 

I am not an expert but you could try that. Check again , but the parameter should be "pci=assign-busses" and not what you wrote.

[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

To enable kernel parameters you edit, /etc/default/grub as administrator, for example like this (in a terminal):

gksudo gedit /etc/default/grub

In this file you will see these lines

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

Change the second one to:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="quiet splash pci=assign-busses"

Save and close, then, in the terminal again:

sudo grub-mkconfig -o /boot/grub/grub.cfg

Reboot. 

Then check if alsa sees your device:

cat /proc/asound/cards

Cheers, Pablo

---

### Post by Mike1962 on 2011-04-01
Thanks I'll try that now!!:KS

---

### Post by Mike1962 on 2011-04-01
[color=red][size=4]thank you!!!

[/size][/color]

---

