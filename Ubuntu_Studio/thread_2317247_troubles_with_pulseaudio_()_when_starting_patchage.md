---
title: "troubles with pulseaudio (?) when starting patchage"
date: 2016-03-14
forum: Ubuntu Studio
---

### Post by Simon_Schler on 2016-03-14
hi all,

although i'm passably familiar with linux in general, i'm not at all experienced with audio and midi on linux yet, so it might be an easy-to-solve issue, but i'm totally stuck with it. Maybe someone has an idea of what could be wrong and how to fix it... 

i did a fresh install of studio 14.04 and after booting, everything is fine (at least the things i tried; being lmms, hydrogen and audacious). As soon as i start patchage (same for QjackCtl), all of them stop playing. i.e. i can still choose between play, pause and and stop, but while "playing", the cursor stays at 0:00 and no sounds are produced. This applies for both audacious and lmms (not sure if i checked hydrogen also).

after closing patchage and killing (=restarting?) pulseaudio, it works again, except for some adjustments being lost (wrong output device and volume).

Any ideas how to fix this? as i want to control some external (hardware-) synths via midi, it would be really convenient to use one of these "gui audio/midi connection tools"..

regards
simon

---

### Post by jejeman on 2016-03-14
First start JACK server, then start applications. Configure applications to use JACK. Switching audio backend in applications usually is not "plug 'n play", it needs manual configurations.
Patchage starts JACK, so it pauses pulseaudio. That is normal. You can "bridge" JACK and pulseaudio, I found it to be buggy, so I don't do it.

---

### Post by Simon_Schler on 2016-03-15
thanks for your reply,
this is somewhat clarifying, but still i don't get it working. Seems i need to get some in-depth knowledge about alsa, jack, and how they interact *before *trying to make use of it... 

e.g. my usb/midi-interfaces all show up as alsa, not jack. In lmms, i can choose between alsa raw and seq, but not jack, and latterly, it alway falls back to dummy (no midi support), and jack doesn't start any more (maybe some configs ruined).

Any hints on reading how to get started on this topic?

---

### Post by jejeman on 2016-03-15
MIDI hardware is always registered as ALSA device. Some applications support both ALSA & JACK MIDI, some just one of them. Don't know about LMMS, obviously it supports ALSA MIDI.
You can bridge ALSA MIDI and JACK MIDI. Search for a2jmidid.

---

### Post by Simon_Schler on 2016-03-15
unfortunately, the computer's network adapter is ruined, so it it time consuming to get and install additional packages; i had expected ubuntu studio with an impressive size of 2.8GB would offer more such stuff out of the box. 

well, i keep on trying ;)

---

### Post by Simon_Schler on 2016-03-16
i read [Ted's Linux MIDI Guide]("http://tedfelix.com/linux/linux-midi.html") now, which was very enlightening to me. guess i got it (-->SOLVED) :)

---

### Post by jejeman on 2016-03-16
Very nice guide (that's what I was talking about ;))
Thanks for the link.

---

