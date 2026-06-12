---
title: "AllInOne, no sound after upgrading from 12.10 to 13.04"
date: 2013-04-27
forum: System76 Support
---

### Post by FreedomOfThought on 2013-04-27
Upgrading to 13.04 went smooth except that I don't have any sounds anylonger.

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
	Subsystem: Intel Corporation Device 2045
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at f7d20000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: snd_hda_intel

aplay -l doesn't give any devices. The sound-test in the system-settings doesn't give any result.

Plesae give any advice, where to look for a solution.

---

### Post by FreedomOfThought on 2013-04-27
Update.

System was hanging at powering down :
ACPID: exiting
speed-dispatcher disbaled
edit: /etc/default/speech-dispatcher

Had to cut the power. After restarting the sound is working.

bernard@Sable:~$ aplay -l
**** Lijst van PLAYBACK hardware-apparaten ****
kaart 0: PCH [HDA Intel PCH], apparaat 0: ALC662 rev3 Analog [ALC662 rev3 Analog]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 0: PCH [HDA Intel PCH], apparaat 3: HDMI 0 [HDMI 0]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0

---

