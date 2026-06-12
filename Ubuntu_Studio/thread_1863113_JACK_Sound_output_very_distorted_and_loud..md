---
title: "JACK Sound output very distorted and loud."
date: 2011-10-17
forum: Ubuntu Studio
---

### Post by rafaelvega on 2011-10-17
Hello. 

I have Ubuntu Studio 11.04, a MacBook Pro 8,1 with the built-in intel HDA sound card and I'm trying to configure JACK for use with Ardour and other audio apps.

Whenever I output any sound through JACK (Using Ardour or Audacious or whatever program that connects to JACK) the sound comes out VERY loud and distorted, you can recognize the audio being played but quality is nothing near acceptable, just plain horrible :S

If I stop JACK and output sound using ALSA (Audacious) or Pulse Audio (Firefox, Flash Player) the sound comes out just fine. Also, recording seems to be fine with JACK (waveforms in Ardour look normal).

I have tried many combinations of parameters in QJackCTL and tweaked levels using Alsamixer but the result is the same.

Here's the output of aplay -l:

rafaelvega@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: Cirrus Analog [Cirrus Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: Cirrus Digital [Cirrus Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by rafaelvega on 2011-10-17
Here are the settings that finally worked for me (latency is terrible but I'll deal with that later, it at all possible). 

Added the following line to /etc/modprobe.d/alsa-base.conf

```
options snd-hda-intel position_fix=1 model=mbp55
```(You have to restart alsa afterwards with ```
sudo alsa force-reload
```)

And started jackd with the following parameters:

```
jackd -dalsa -Strue -p4096
```

---

