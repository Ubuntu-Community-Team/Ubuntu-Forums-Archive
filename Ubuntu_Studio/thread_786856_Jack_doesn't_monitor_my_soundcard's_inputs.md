---
title: "Jack doesn't monitor my soundcard's inputs"
date: 2008-05-08
forum: Ubuntu Studio
---

### Post by virgult on 2008-05-08
Hi everybody.
I've installed Hardy Heron right now, on my P4 3.0 ghz with 1.5 gbs of RAM and a Terratec Phase 22 soundcard (the chipset is something like the ICE1724). With Ubuntu Gusy everything under Jack used to go fine, including the direct monitoring of the inputs - a thing that i love, it lets me play along with the songs my PC plays! ;)
But with Hardy something strange occurs: I installed Jack with Qjackctl, set up the correct realtime limits in /etc/security/limits.conf, the server starts and it's up and running, but... when I try to connect the input directly to the output via Jack, no sound comes out. As well, it seems that Ardour isn't able to record the signal of my inputs anymore. What happened, and how can I fix that?

Some clues:
- Qjackctl messages
```
18:56:19.488 Patchbay deactivated.
18:56:19.640 Statistics reset.
18:56:19.676 ALSA connection graph change.
18:56:19.860 ALSA connection change.
18:56:44.543 Startup script...
18:56:44.545 artsshell -q terminate
sh: artsshell: not found
18:56:44.951 Startup script terminated with exit status=32512.
18:56:44.952 JACK is starting...
18:56:44.952 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p256 -n2
18:56:44.984 JACK was started with PID=6173.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|256|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 256 frames (5.8 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
18:56:47.065 Server configuration saved to "/home/virgult/.jackdrc".
18:56:47.068 Statistics reset.
18:56:47.121 Client activated.
18:56:47.125 JACK connection change.
18:56:47.132 JACK connection graph change.
```

- In "connections" window, the two main inputs and outputs are no more called "Alsa_PCM", as they were in Gutsy, but simply "system". Does it mean anything?

Please, help a young rocker in his way to stardom. :guitar: :lolflag:

---

### Post by virgult on 2008-05-11
SOLVED - The volume levels of the two inputs were set at 0, I set the right values through alsamixer.

---

