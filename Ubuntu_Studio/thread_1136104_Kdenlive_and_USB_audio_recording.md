---
title: "Kdenlive and USB audio recording"
date: 2009-04-24
forum: Ubuntu Studio
---

### Post by sleepingdragon on 2009-04-24
Hey. I've been kicking around with this problem since I installed Jaunty - everything is working great except I cannot record audio through my USB Logitech webcam in Kdenlive. Audio is working through Pulse.

The audio works as normal in all other apps like Skype and Audacity and they record just great. However, Kdenlive is giving me nothing but a nasty buzz on audio. Does anyone know what the settings are in Kdenlive to initialise USB audio? So far, the only combos that do anything (in Capture Configuration) are:

device: /dev/dsp1 Format: OSS
device: /dev/dsp1 Format: ALSA
device: plughw:DEV=0,CARD=1 Format: ALSA

Everything else I can think of stops Kdenlive from attempting to record altogether. I've also tried specifying the bitrate and frequency parameters to the defaults in case that was not being picked up automatically - but there's no change.

Any help would be greatly appreciated! I'm off to bed now - any more views of my ugly mug doing buzzy mime impressions and I'm gonna go mad!

---

