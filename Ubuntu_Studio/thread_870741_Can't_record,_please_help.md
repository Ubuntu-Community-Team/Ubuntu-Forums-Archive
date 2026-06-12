---
title: "Can't record, please help"
date: 2008-07-26
forum: Ubuntu Studio
---

### Post by Abstract Zzzxyz on 2008-07-26
Okay, here's my recording saga:

I've been a happy Linux-convert since June(hardy)-previously used Cool Edit Pro in XP. The whole 'back-end/front-end-thing' is very new for me. I've tried Audacity, Ardour, and Traverso (i think i like Traverso even more than Ardour), but in each program, I can PLAY wavs, but can't RECORD. The problem seems to either be my soundcard (on-board Crystal Fusion cs46xx) or maybe the way I've set up ALSA. (even re-installed ALSA per Ubuntu direction)

Please don't tell me to un-mute everything in Volume Control or Alsamixer-done that. I've tried different device setups in Vol ctl (do we really need alsa, jack, oss and pulseaudio? very convoluted) and different ways of setting up Jack. Each time the same: play-good, record-bad. I even tried just recording something in 'Sound Recorder'-nope. . .

And yes, my actual audio connections are fine, I can tap on the mic, and hear it, just can't capture. I'm using a very nice mic/mic preamp into my line-in.

Help.

---

### Post by Robertjm on 2008-07-26
When you open Alsamixer go to the Switches tab. Make sure that Line-In Capture is checkmarked.

If you have a Recording tab make sure all mic symbols don't have red marks on them.

What devices do you show listed in your Alsa Mixer? If you can't use the firest setting, I don't have Hardy installed on my computer anymore, but it seems to me that I have both sblive and OSS listed. A few installs ago I had to use the OSS device to be able to see the PCM2 setting to control playback volume every time I switched to KDE.

BTW: Have you tried hooking the mic directly to a mic input connector (if your computer has such an input)?

Good luck! 

Robert

---

### Post by Abstract Zzzxyz on 2008-07-26
Yep, line-in capture is checked. and yes, everything is unmuted/enabled/turned up.

here's what's listed in alsamixer: (this may not be what you were talking about)
Card: Sound Fusion CS46xx
Chip: Cirrus Logic CS4297 rev3
View: [Playback] Capture All
Item; (whatever fader is selected below)

THEN, here's the devices listed in Volume Control:
0: Sound Fusion CS46xx (alsa mixer)
1: Cirrus Logic CS4297 rev3 (OSS mixer)
2: Playback: ALSA PCM on front:0 (cs46xx) via DMA (Pulseaudio mixer)
3: Capture: Monitor source of ALSA PCM on front:0 (cs46xx) via DMA (Pulseaudio mixer)
4: Capture: ALSA PCM on front:0 (cs46xx) via DMA (Pulseaudio mixer)

I've tried ALL of them, with every possible fader and switch unmuted, enabled, checked, and turned up. Aaaaaaagh! It shouldn't be this hard!

and yep, I've also tried plugging into my soundcard's MIC-in for fun(or, not)- nothing. If the REAL answer is a new soundcard, I'll just have to wait til I trip over that descretionary income I always leave lying around, and buy a new one. sigh.

---

### Post by Robertjm on 2008-07-26
Just double checking...Do you have any listing labeled as "Alsa Default" for capture devices? I only get sound out of my setup when I have mine set to that one.

Robert

---

### Post by djxcon on 2008-07-26
When you start up Jack (I am assuming that you have installed qjackctl), do you see any readable clients in the Connect menu?  You will have to expand the System section (left hand side) and it should list the readable clients on your sound card.  If you do, then I think this is a good place to start.

Then we will need to hook up the readable side to a program that can write the audio information. 

Also, do you only have one sound card in your system?

---

