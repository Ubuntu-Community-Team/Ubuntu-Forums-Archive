---
title: "No USB sound devices listed/recognized"
date: 2013-09-15
forum: Ubuntu Development Version
---

### Post by zika on 2013-09-15
I was messing with my Saucy install and I've lost all USB sound devices from ALSA/Pulseaudio/Gstreamer...
They are fully recognized if I boot from LiveCd (Saucy and update/upgrade to same state as install on HD...) so HW is working OK...
None of several USB sound DAC's is being seen/recognized...
Sound works OK through Radeon and through built-in-audio (S/PDIF)...
I might have erased something that in fact is needed (cleaned via gtkorphan as I do on many occasions), but I doubt that that is what have happened...
```
:~$ lsusb
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 004: ID 0b95:772a ASIX Electronics Corp. AX88772A Fast Ethernet
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 08bb:2706 Texas Instruments PCM2706 Audio Codec
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
As You can see USB PCM2706 (for example) is recognized by system. It is only not recognized by ALSA and hence by PulseAudio...
```
:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
Any ideas?

Update&#8321;: I founf solution... Somehow in file /etc/modprobe.d/alsa-base.conf line```
sna_usb_audio: index=-2
```resutfaced again. Commenting it out solved the problem...
Also, just in case```
modprobe -a snd-usb-audio
```was performed... Now it remains to be seen if it survives reboot...
As they say: morning is smarter than midnight...

Update&#8322;: It works...
Long live my notebook (paper, old-school) logs...
Marking this SOLVED...

---

