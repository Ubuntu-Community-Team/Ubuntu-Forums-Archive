---
title: "having trouble with Jack xruns"
date: 2008-04-25
forum: Ubuntu Studio
---

### Post by kragen on 2008-04-25
I'm having problems with xruns using Jack, real time mode is enabled (and working as far as I can tell), priority is set to 70, like everyone seems to recommend, and yet my audio sounds really bad even at 1024 frames.

I've also tried Force 16bit and... well pretty much every combination that I can think of.

Its just a normal sound card (the one on my motherboard), but I've managed to get it working great before.

I've posted the log from when it starts up below:
To be honest, its been a while since I've done this - if anyone could help explain anything it would be really handy, like what is memlock?

```
20:56:07.646 /usr/bin/jackd -R -dalsa -dhw:0,0 -r48000 -p1024 -n2 -D -Chw:0,2
20:56:07.649 JACK was started with PID=6667.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0,0|hw:0,2|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
**** alsa_pcm: xrun of at least 0.027 msecs
20:56:09.795 Server configuration saved to "/home/justin/.jackdrc".
20:56:09.797 Statistics reset.
20:56:09.803 Client activated.
20:56:09.810 JACK connection change.
20:56:09.814 JACK connection graph change.
```

---

### Post by kragen on 2008-04-25
Btw, I've just tried "Soft Mode" with very little effect - it looks like your getting less xruns in qjackctl, but its just as bad in jack.

Its probably worth noting, the RT indicator is flashing between lit and grayed out - what does that mean?!

---

### Post by kragen on 2008-04-25
Well, its working now for some reason, no idea why - I just changed a few settings, but changing them back doesn't seem to break it again.

Oh well, would have been nice to figure out what I was doing wrong!

---

