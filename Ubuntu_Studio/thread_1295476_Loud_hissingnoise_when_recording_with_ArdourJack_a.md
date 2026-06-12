---
title: "Loud hissing/noise when recording with Ardour/Jack and Edirol UA25"
date: 2009-10-19
forum: Ubuntu Studio
---

### Post by blafasel1234 on 2009-10-19
Hi everybody,

some days ago I started a new attempt with audio recording using UbuntuStudio 9.04 and Ardour. As audio interface I'm using an Edirol UA25 USB interface with my notebook (1.4GHz, 1GB RAM).

Recording and playing sounds via ALSA seems to work fine, at least
```
 arecord -r 96000 -f cd -t wav -D plughw:UA25 test.wav
```and
```
aplay -D plughw:UA25 test.wav
``` worked as expected.

However, recording in Ardour via Jack gives only loud hissing and noise (the to-be-recorded signal can be heard only very silent in the "background" of the noise). Playing sounds from Ardour via the Edirol works perfectly fine, as well as routing sounds from e.g. Hydrogen to Ardour, so I guess that it's a problem only between the Edirol and the Jack/ALSA. Trying different settings at the Edirol and/or at Jack didn't help, so I'm pretty helpless for now how to fix this.

Here are my current settings at the Edirol:

[LIST]
[*]Sampling rate: 44.1kHz
[*]Advanced mode: On
[*]Play/Record: Record
[/LIST]
My current Jack settings (I'll also try to attach an according screenshot of Qjackctl):
[LIST]
[*]Realtime: On
[*]Monitor: On
[*]Frames/Periode: 128
[*]Sampling Rate: 44100
[*]Periods/Buffer: 3
[*]Port Maximum: 256
[/LIST]
I'd be so happy if somebody might give me a hint how to solve this problem. For now, I'm really helpless... :confused:

Thanks a lot and regards from Munich,

Uli

---

### Post by AutoStatic on 2009-10-20
Hello Uli, I have the exact same device and no problems with it. But I don't use Ardour, I prefer Qtractor.
My JACK settings:
[LIST]
[*]Realtime: On
[*]No Memory Lock: On
[*]Monitor: Off
[*]Frames/Periode: 64
[*]Sampling Rate: 48000 (the UA-25 likes this sampling rate best)
[*]Periods/Buffer: 3
[*]Port Maximum: 256
[/LIST]

So the latency is 4ms. Yesterday I recorded a few new ideas and I had zero xruns on my system and sound quality is excellent. But how do you route your inputs from the UA-25? System - capture 1 is the left channel (channel 1) and system - capture 2 is the left channel (channel 2). You can route these seperately within JACK.

---

### Post by ryanisablond on 2009-10-20
Hi blafasel1234, sorry to hear about your problem. Do you know for a fact that your audio interface is working? I had an op-amp die in my Apogee Duet a year ago and it would only record a "hissing static" sound that reminds me of what you describe. 

I really hope that isn't your problem, but at least it would cross one possibility off the list. 

Good luck!

---

### Post by Zimmer on 2009-10-20
[http://www.vimeo.com/2867399](http://www.vimeo.com/2867399)

Might be some help there, I did notice in a link somewhere that you need to enable recording on each channel mixer control before actually pressing the main recording button...

It might be why I had no luck with Ardour (wiped it when I upgraded to 9.04 BTW).

I got frustrated with JACK,too so I do not have Ardour installed currently to check...

---

### Post by solarbird on 2009-10-21
...do you have another sound card *of any kind* in the computer? Does it have a microphone *of any sort* on it?

When you record in Ardour, what kind of signal response are you seeing on the mixer metres?

See, I have a suspicion that you have another sound card (probably built in, probably on motherboard) and Ardour is looking at that for input rather than looking at your USB microphone, and it's picking up the same signal but from a much, much worse position. It could be even just picking up leakage through the speakers if it doesn't have another microphone.

So go look at Ardour, in mixer view (or with the single-track mixer showing on your editing board, either is fine) and check what inputs are going into that track. You'll have a lot of options, and I suspect Ardour is grabbing the wrong device.

Actually this could sorta-kinda happen even if there isn't another sound card, so check regardless. (It could be picking up input from another track or application or something. Unlikely but we're looking at that now.)

Anyway, try that, and see if that makes the problem's source clearer.

---

### Post by mesrumma on 2009-11-30
Hi, I also have a noise Problem using Jack on Ubuntu-Studio 9.10. When I force using 16 bit everything works fine. You can easily check if it's a problem with Jack by connecting an input with an output channel.
You better turn down the volume a little, it nearly blew out my ears.

Ok, this is Jack output with noise: 

```
18:04:32.880 Startup script...
18:04:32.882 artsshell -q terminate
sh: artsshell: not found
18:04:33.336 Startup script terminated mit Rückgabewert = 32512.
18:04:33.337 JACK startet...
18:04:33.338 /usr/bin/jackd -R -P80 -dalsa -r44100 -p64 -n4 -D -Cplughw:0 -Pplughw:0 -i8 -o2
18:04:33.442 JACK wurde mit PID = 9825 gestartet.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... plughw:0|plughw:0|64|4|44100|8|2|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 64 frames (1.5 ms), buffer = 4 periods
ALSA: final selected sample format for capture: 32bit float little-endian
ALSA: use 4 periods for capture
ALSA: final selected sample format for playback: 32bit float little-endian
ALSA: use 4 periods for playback
18:04:35.653 Serverkonfiguration nach "/home/fu/.jackdrc" gespeichert.
18:04:35.656 Statistik zurückgesetzt.
18:04:35.661 Client aktiviert
18:04:35.676 JACK-Verbindung geändert.
18:04:35.698 Schaubild der JACK-Verbindungen geändert.
18:04:35.992 JACK active patchbay scan...
```This is Jack output with forced 16 bit and no noise:

```
18:02:36.738 Startup script...
18:02:36.740 artsshell -q terminate
sh: artsshell: not found
18:02:37.180 Startup script terminated mit Rückgabewert = 32512.
18:02:37.181 JACK startet...
18:02:37.182 /usr/bin/jackd -R -P80 -dalsa -r44100 -p64 -n4 -D -Cplughw:0 -Pplughw:0 -S -i8 -o2
18:02:37.198 JACK wurde mit PID = 9663 gestartet.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... plughw:0|plughw:0|64|4|44100|8|2|nomon|swmeter|-|16bit
control device hw:0
configuring for 44100Hz, period = 64 frames (1.5 ms), buffer = 4 periods
ALSA: final selected sample format for capture: 16bit big-endian
ALSA: use 4 periods for capture
ALSA: final selected sample format for playback: 16bit big-endian
ALSA: use 4 periods for playback
18:02:39.496 Serverkonfiguration nach "/home/fu/.jackdrc" gespeichert.
18:02:39.499 Statistik zurückgesetzt.
18:02:39.587 Client aktiviert
18:02:39.590 JACK-Verbindung geändert.
18:02:39.602 Schaubild der JACK-Verbindungen geändert.
18:02:39.947 JACK active patchbay scan...

```[FONT=monospace]
I hope this helps some of you working around the bug or even repairing it.
Thank you,
regards,
mesrumma
[/FONT]

---

### Post by AutoStatic on 2009-11-30
Hello mesrumma, do you own an Edirol UA-25 yourself?

---

### Post by mesrumma on 2009-11-30
No, I don't own an Edirol, but a M-Audio Delta1010lt (ice 1712). I just thought it might be the same problem and I found only few posts about it. Let's see if it helps blafasel1234 to force 16 bit, then it's the same problem and doesn't depend on the device.

---

