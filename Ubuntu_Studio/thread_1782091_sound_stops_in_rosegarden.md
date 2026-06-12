---
title: "sound stops in rosegarden"
date: 2011-06-14
forum: Ubuntu Studio
---

### Post by ccaaee on 2011-06-14
Hi

I'm using ardour, hydrogen and rosegarden/qsynth through jack and am having a recurring problem with rosegarden.  For no apparent reason I loose all sound after such things as resizing a track etc.
The horizontal bar graphs at on each track give a visual indication of midi activity but I have to restart rosegarden in order to hear something.

Any Ideas ???

thanks 

C

---

### Post by Pablo_F on 2011-06-14
Version numbers please :)

---

### Post by ccaaee on 2011-06-15
Sorry

Ardour 2.8.6
Hydrogen 0.9.4
Rosegarden 10.02
jack 0.3.4
qsynth 0.3.4

In the meantime I noticed that the midi link from rosegarden to qsynth (fluid synth) had disappeared in ALSA tab in Jack...  Reconnecting it brought back the sound. The next time this happens I'll take a look at the jack logs.

C

---

