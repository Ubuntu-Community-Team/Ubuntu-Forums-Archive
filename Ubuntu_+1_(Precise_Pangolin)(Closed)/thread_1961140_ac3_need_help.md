---
title: "ac3 need help"
date: 2012-04-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by xzero1 on 2012-04-18
Using the following command line I get a 5.1 ac3 signal (according to my external amp) even though in reality it is (incorrectly) mixed to the two front speakers only:

```
mplayer -v -ao alsa:device=hw=1.2 -ac hwac3 test.ac3
```

 I suspect this is may be an mplayer regression since this is the same in Lucid.


When I use gstreamer-properties using apparently the same settings i.e. : (audio plugin:alsa, device: C-Media PCI IEC958, [dimmed]-> Pipeline: alsasink device="hw:1,2") and test I get no sound. Note that setting gstreamer-properties to pulse gives normal sound.

This device should be the correct according to aplay -l. I only use the C-Media card.

```
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8768 [C-Media CMI8768], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8768 [C-Media CMI8768], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8768 [C-Media CMI8768], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Trying another method: [https://help.ubuntu.com/community/DigitalAC-3Pulseaudio]("https://help.ubuntu.com/community/DigitalAC-3Pulseaudio")

...after getting the proper source to compile, the install plugin section seems out of date (For Oneiric Ocelot (11.10) or Later). Where do I copy the a52 libs?

Update: It seems it goes (in my case to) to: /usr/lib/x86_64-linux-gnu/alsa-lib/
I now get sound using:
```
speaker-test -c6 -D a52:1
```
But the sound only comes out of the two front speakers as was the case before. Is this a configuration issue or simply a bug? It seems something is downmixing the sound to 2 channel.


Is there a way to play ac3 multichannel files via spdif on precise?

---

