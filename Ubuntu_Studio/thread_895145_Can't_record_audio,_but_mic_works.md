---
title: "Can't record audio, but mic works"
date: 2008-08-19
forum: Ubuntu Studio
---

### Post by fauzie on 2008-08-19
Hi, I'm unable to record audio from any source with any program. However the microphone is working well, I can hear the sound from the mic going through my speakers if I unmute AMic (from alsamixer), but nothing can get recorded. I've tried audacity, sound recorder, and rosegarden with all available settings, none worked. The best thing I can get is to make rosegarden records its own metronome, which is quite useless.

I'm using Ubuntu 7.10, without pulseaudio (I noticed most people get problems with that). The soundcard is Audigy2. I've unmuted and set everything to maximum from alsamixer. I especially need audacity to work ASAP. Recording on this system worked before with Gentoo.

Any advice?

---

### Post by Creative2 on 2008-08-20
sudo apt-get install sox libsox-fmt-all

then try with audacity

---

### Post by eye208 on 2008-08-20
This is a well-known problem. See here for a solution:

[http://ubuntuforums.org/showthread.php?p=4273030#post4273030](http://ubuntuforums.org/showthread.php?p=4273030#post4273030)

---

### Post by fauzie on 2008-08-20
Thanks for the quick reply. It fixed the problem.

My alsamixer setting:
Playback: 
Master 100%
Bas 100%
Treble 100%
Surround 100%
LFE 100%  (it has something to do with the way my speakers are connected)
Synth 100%
Wave 100%
Mic select Mic 1
AMic 100%
Analog Mix 100%
Audigy A  unmute

Capture:
Master 100%   Capture
Bas 100%
Treble 100%
Mic 61%  Capture
Analog Mix 100%

Audacity setting:
Audigy Capture / Standard PCM Playback for both playback and recording
Channels 1 (Mono)
Checked Play other tracks while recording new one

I figured I had to set Capture on both Master and Mic.

Time for some music
:guitar:

---

### Post by oliviajohn on 2008-08-21
Hi eye208,

          Thanks for giving solutions!

---

