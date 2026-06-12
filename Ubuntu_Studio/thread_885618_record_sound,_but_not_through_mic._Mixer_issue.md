---
title: "record sound, but not through mic. Mixer issue"
date: 2008-08-10
forum: Ubuntu Studio
---

### Post by Statix83 on 2008-08-10
Howdy,

I'm trying to record anything coming out of my speakers but am currently only getting what my inbuilt mic picks up (not terribly great and includes external noises)

From what I've read I need to change settings in my "mixer" or something though I never quite see the specific options that people mention, like 'mix' or 'mix mono' etc

All I really want to do is change my capture device from my internal mic to something else (speaker??)

I don't mind using vlc and specifying which /dev/thingy to capture from if I knew which to use (assuming that would work?)

**Details:**
Dell XPS M1530
Ubuntu 8.04
Alsa 1.0.15
**currently recording using:**
   arecord -f cd output.wav
**Tick boxes available in Volume control preferences:**
[x]Master 
   Headphone as line out
[x]PCM 
[x]Front 
   Surround
   Center
   LFE
   IEC958
   Capture
   Capture 1
   Capture 2
   Analogue Loopback
[x]Digital 
[x]Digital Input Source 
   Input source
   Input source
   Input source
   Mux
   Mux 1
   Mux 2
   Swap Center/LFE

I've tried various combinations of input source/capture tracks and don't really know what I'm doing.

In volume control, the options tab gives me a choice of digital mic 1 and analogue inputs.
Digital mic 1 seems to be the inbuilt mic, analogue inputs doesn't do much so will assume for now its line in.

---

