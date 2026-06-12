---
title: "No sound with JACK in Ubuntu Studio"
date: 2008-10-08
forum: Ubuntu Studio
---

### Post by fernandoguitar on 2008-10-08
Hello everybody, (excuse my english). I am new in Linux, Ubuntu Studio OS and I have problems with JACK. I run JACK but don't get sound from Rosegarden, Ardour and any other audio applications. But when JACK isn't running  sound comes through fine. This is the results in messeges...Thank for your help.


04:34:53.308 Patchbay deactivated.
04:34:53.623 Statistics reset.
04:34:53.742 Startup script...
04:34:53.744 artsshell -q terminate
04:34:53.769 ALSA connection graph change.
04:34:54.845 Startup script terminated with exit status=256.
04:34:54.848 JACK is starting...
04:34:54.850 /usr/bin/jackd -R -P60 -dalsa -dhw:0,0 -r44100 -p64 -n4 -m -S
04:34:54.861 JACK was started with PID=15804.
04:34:55.060 MIDI active patchbay scan...
04:34:55.109 ALSA connection change.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
04:34:55.311 MIDI active patchbay scan...
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0,0|hw:0,0|64|4|44100|0|0|nomon|swmeter|-|16bit
control device hw:0
configuring for 44100Hz, period = 64 frames (1.5 ms), buffer = 4 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 4 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 4 periods for playback
04:34:57.177 Server configuration saved to "/home/fernando/.jackdrc".
04:34:57.189 Statistics reset.
04:34:58.331 Client activated.
04:34:58.340 JACK connection change.
04:34:58.419 JACK connection graph change.
04:34:58.545 Audio active patchbay scan...
04:36:56.896 JACK connection graph change.
04:36:56.999 Audio active patchbay scan...
04:37:00.357 JACK connection graph change.
04:37:00.470 Audio active patchbay scan...
04:37:00.480 JACK connection change.
04:37:00.683 Audio active patchbay scan...
04:37:00.726 JACK connection graph change.
04:37:00.774 ALSA connection graph change.
04:37:00.892 Audio active patchbay scan...
04:37:00.896 MIDI active patchbay scan...
04:37:00.909 ALSA connection change.
04:37:01.115 MIDI active patchbay scan...
04:37:10.025 JACK connection graph change.
04:37:10.160 Audio active patchbay scan...
04:37:10.167 JACK connection change.
04:37:10.371 Audio active patchbay scan...
04:37:10.497 ALSA connection graph change.
04:37:10.578 MIDI active patchbay scan...
04:37:10.584 ALSA connection change.
04:37:10.788 MIDI active patchbay scan...

---

### Post by markbuntu on 2008-10-09
Well, it seems that jack is up and running. Can we get a screenshot of the jackcontrol setup page?

---

### Post by fernandoguitar on 2008-10-10
> **markbuntu said:**
> Well, it seems that jack is up and running. Can we get a screenshot of the jackcontrol setup page?

Thank you for you response. This is screenshot of all tabs in the setup.

---

### Post by markbuntu on 2008-10-10
Try changing Interface from hw:0,0 to to hw:0 or to default. See if that works.

---

### Post by fernandoguitar on 2008-10-11
> **markbuntu said:**
> Try changing Interface from hw:0,0 to to hw:0 or to default. See if that works.

Thank you JACK is working now with many applications except with Rosegarden. But I am happy with the progress. So thank you very much and regards for all ubuntu community

---

### Post by robeast on 2008-10-11
If you are using MIDI in Rosegarden you need to either route the MIDI signals to a softsynth or setup a softsynth for that track in Rosegarden if you want to hear it.

---

