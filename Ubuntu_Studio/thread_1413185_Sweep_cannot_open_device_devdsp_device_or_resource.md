---
title: "Sweep: cannot open device /dev/dsp: device or resource busy"
date: 2010-02-22
forum: Ubuntu Studio
---

### Post by temcat on 2010-02-22
Hi all,

I'm trying to get sound out of Sweep editor to no avail. I have a Jaunty setup with Alsa output routed through Jack. Every time I try to play something using Sweep, a window pops up saying "Cannot open device /dev/dsp: Device or resource busy".

First of all, nothing seems to hold the /dev/dsp device, as shown by "lsof | grep dsp".

I know that /dev/dsp is related to the deprecated OSS sound system. I modprobed snd_pcm_oss, snd_mixer_oss and snd_seq_oss modules, but it didn't help.

In Sweep's Playback -> Configure audio devices, I tried to manually enter /dev/snd/pcmC0D0p, /dev/snd/pcmC0D0c, and /dev/snd/pcmC0D1p as sound devices instead of /dev/dsp, but then Sweep either hung or silently died when trying to play.

Stopping Jack doesn't help either.

Can anybody help? I currently have to reboot to Vista to edit the file I recorded in Linux, which is a bit silly...

Update: I kinda got it to play using "aoss sweep [filename]", but it is unstable that way.

---

### Post by a z on 2012-01-13
bump
hey, i 'd like to get sweep running too (Lubuntu). it opens, and loads a pre-existing wav or mp3, just won't play it (the dev/dsp thing). sweep has a mix-paste feature that i can't find in audacity, so would be worth keeping around, if only for that. 
??? Ubuntu keeps this semi-functioning app, buts dumps rezound???

---

