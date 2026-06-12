---
title: "Can't record audio: Ubuntu Studio 8.10, Dell Inspiron"
date: 2009-03-07
forum: Ubuntu Studio
---

### Post by nothinghappens on 2009-03-07
I've never been able to record audio on this Dell Inspiron 1420N for as long as I've had it.  I bought it a little under a year ago with Ubuntu installed, I think it came with Gutsy.  I've upgraded to Hardy, then to Hardy Studio, and now Intrepid Studio.  Never in all this time have I successfully captured and recorded audio.  Every so often I resolve to try one more time to get it to work, and try every conceivable setting in alsamixer, audacity, etc. -- to no avail.

Here's lspci, if that helps:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)                                                                                                   


A few little notes:

 - No problems with playback ever.  I can listen to music, watch videos online, whatever.

 - The 1420N has three jacks on the front: one with a headphones symbol next to it (the headphone jack obviously), one unlabeled (possibly line-in?  Can't seem to get it to do anything), and one with a microphone symbol next to it (seems to be the mic input)

- alsamixer (using the gnome one) seems to think I have a SigmaTel STAC9228 -- I'm not sure if this is the same thing as Intel 82801H or not

 - If I connect an audio source to the microphone input and crank up the "capture" and "Mux" sliders in alsamixer far enough, I can very faintly hear the audio I'm playing into it, underneath a load of hiss.  Also, I hear popping when I connect the input (of the expected something's-being-plugged-in variety), but also hear popping (of some other sort) while moving these sliders.  And incidentally, it's a line-level signal I'm connecting there, so if anything it ought to be too loud, not too soft.

 - Yes, I'm sure the cable I'm connecting the audio source with is good.

---

### Post by clubsoda on 2009-03-31
It's not enough just to set the level, you have to choose the input as well.  In alsamixer, press Tab until [Capture] is highlighted under View:
Then use the left/right arrows to highlight the input you want to record and press the space bar to activate.  A red "L R CAPTURE" should appear.  The inputs which can be selected are indicated by "-----" under the level sliders.
Hope this helps.

---

### Post by markbuntu on 2009-04-02
The Dell Inspirion 1420N is listed here along with directions for getting the sound driver working correctly. This should fix your mic problem.

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

