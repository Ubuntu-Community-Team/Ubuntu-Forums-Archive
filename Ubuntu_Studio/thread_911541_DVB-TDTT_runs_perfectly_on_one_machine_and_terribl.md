---
title: "DVB-T/DTT runs perfectly on one machine and terrible on another"
date: 2008-09-05
forum: Ubuntu Studio
---

### Post by yadayada2 on 2008-09-05
Hello over there,

I have a problem related to my Acer Aspire L5100 (stationary PC) and my notebook in use with Me-TV.

The thing is, I have a TerraTec Cinergy T USB XS FM Hybrid stick for reception of DVB-T/DTT. On my notebook I use Xubuntu 8.04 and everything works fine with Me-TV as well as with Kaffeine and Gxine. The system is up to date.
On the other hand there is my stationary PC, which was actually intended to be used with that USB stick. Here I run Ubuntu 8.04 and the system is up to date, too. However, no matter what program I use (Me-TV, Kaffeine, Gxine) the channels appear, but the signal shows some distortions. I think, those colourful blocks are called artefacts. There are annoying sounds like "glb", too. Sometimes the sound crashes at all.

As for now, I have not the slightest idea, what might trigger this different behavior. I have even set the stationary PC next to the laptop and I let the antenna remain where it was while pluging in the usb stick from one to another machine.
The driver for the stick was installed the same way according to the corresponding installation guide from mcentral.de.

I guess, you need some information about the hardware. The stick has the ID 0ccd:0092 (I have that one from lsusb).

lspci on the stationary pc says:

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

Can this have something to do with the ATI radeon? I really have no clue, what might distort this signal only on this computer. I even connected the drive via an usb extension cable to make sure that the problem has nothing to do with pluging the stick in directly into the PC. Same difference.

Thanks for all your help!

---

### Post by yadayada2 on 2008-09-06
Push

---

### Post by Erlander on 2008-09-07
Two possibilities come to mind.

The usb port on your stationary pc may not be delivering enough current to fully power the tuner.  The fix is to use a powered usb hub.

the second is easier to check.  PC's and their power supplies in particular radiate radio frequency interference.  This can affect the recption through tv tuner cards and usb tuners.  Try moving the tuner further away from the pc with a usb cable.

Rob

---

