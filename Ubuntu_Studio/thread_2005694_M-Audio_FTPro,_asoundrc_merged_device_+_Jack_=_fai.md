---
title: "M-Audio FTPro, asoundrc merged device + Jack = fail"
date: 2012-06-18
forum: Ubuntu Studio
---

### Post by dewdrop_world on 2012-06-18
Apologies in advance to anybody on the Linux Audio Users mailing list, if you already saw that question over there. The issue is becoming a bit of a thorn in my side. On the one hand, I'm told that it should be straightforward to merge devices if they are properly clock-synced. On the other hand... it's not working.

I'm trying to configure Jack 1.9.6 on Ubuntu 10.04 (with real-time kernel) to use all four channels of an M-Audio fast track pro. The class-compliant USB audio driver reads a pair of stereo devices:

```
card 1: Pro [FastTrack Pro], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Pro [FastTrack Pro], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```I've set up a merged device in .asoundrc -- [http://pastebin.com/zr4QuwZj](http://pastebin.com/zr4QuwZj) -- and tested directly against alsa, no problem:

1. Play a stereo, 44.1 kHz, 16 bit file to hw:1,0 using aplay.
2. Play the same file to hw:1,1.
3. Use SuperCollider to make a four channel version of the same file, and play this to the merged device.

All of these tests are successful -- so I think the .asoundrc configuration is correct.

Jack can use either of the stereo devices -- hw:1,0 or hw:1,1 -- for playback with no problem. I've been using that successfully for almost two years now.

But... (-Chw:1,1 is for the FTPro's stereo input)

```
/usr/bin/jackd -S -P60 -dalsa -r44100 -p1024 -n2 -D -Chw:1,1 -Pft4 -s
```... gives me:

```
JACK server starting in realtime mode with priority 60
audio_reservation_init
Acquire audio card Audio1
creating alsa driver ...
   ft4|hw:1,1|1024|2|44100|0|0|nomon|swmeter|soft-mode|32bit
Using ALSA driver USB-Audio running on card 1 - M-Audio FastTrack Pro at usb-0000:00:1d.0-1.5, full speed
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
ALSA: could not start playback (Broken pipe)
Cannot start driver
JackServer::Start() failed with -1
Released audio card Audio1
audio_reservation_finish
Failed to start server
```Any ideas what I'm missing?

BTW, I have already tried alsa_out, but it's really unacceptable for live concert use. To make it practical, I would have to guarantee that I can have my setup switched on and running for at least five minutes before playing (and there's no way to guarantee that in every situation -- concerts are often chaotic), AND if the audio system goes wonky any time between setting up and playing and you have to restart jack, it's another at least five minute delay before it's ready to play. Heaven forbid you crash on stage.

I had seen the other thread about Jack with multiple sound cards and the recommendation to use alsa_out, but that won't work for me. Just mentioning it so that nobody wastes their time by posting about that here.

Thanks in advance,
hjh

---

### Post by dewdrop_world on 2012-06-18
Oh, F******** :shock::mad:

[http://lalists.stanford.edu/lau/2010/09/0194.html](http://lalists.stanford.edu/lau/2010/09/0194.html)

> It seems that my new laptop has a buggy USB controller (lspci says  'Intel Corporation 5 Series/3400 Series Chipset USB2') and this causes  JACK to fail in 'duplex mode' and 'only recording mode'

```
lspci | grep USB

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)

```

OK, never mind, I have to buy something extra now to make this work.

---

### Post by sgx on 2012-06-18
Hi, a mixer with line out might be fine for the working stereo input, and supply other useful features for performance tweaking.

Might want an older desktop and cheap lcd, for chaotic concerts.
mAudio pci cards are simple and widely compatible. New laptops
would be my very last choice for a linux setup, since time is
needed for new chipsets to get kernel support. :popcorn:

---

