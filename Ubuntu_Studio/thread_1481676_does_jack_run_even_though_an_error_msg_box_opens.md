---
title: "does jack run even though an error msg box opens?"
date: 2010-05-12
forum: Ubuntu Studio
---

### Post by jangal on 2010-05-12
context= i'm a noob. 

so does jack run even though an error msg box opens? my situation consists of running ubuntu 10.4 (with mini-studio = laid out in *ubuntu studio preparation* by scott, which is pretty sick) on a dell xps m140. 

every time i run jack an error box opens up saying "jack sever cannot connect", i hit ok, and the display shows that it is running. i connect ardour, hydrogen, etc and all *work. *my question is: why does the error box appear? and am i really in real time mode (how do you calculate/feel milliseconds?)?

thnx,
jangal

---

### Post by sgx on 2010-05-13
Hi, messages and errors often appear when starting apps,
its even good to try starting a problem app from the terminal, as hints to its problem may be revealed there.
Try this from a cold start. From a terminal, start jackd with this

jackd -R -d alsa -r 44100

The last line of terminal output should be a lot like this:

ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback

If so, start qjackctl, press its start button, see if there is an RT
or R 
flashing slowly in the top row of the gui, indicating 'realtime' is functioning.

Cheers

---

### Post by jangal on 2010-05-13
yes. the lines appear in terminal as you say and RT is flashing. thank you very much - jangal

---

