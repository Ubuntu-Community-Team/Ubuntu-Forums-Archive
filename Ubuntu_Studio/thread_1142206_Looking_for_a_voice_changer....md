---
title: "Looking for a voice changer..."
date: 2009-04-29
forum: Ubuntu Studio
---

### Post by higashi on 2009-04-29
Hay,

I'm looking for a sound editor/ voice changer that can give the whole "Southpark" effect on voices (the way the kids sound).

How can i achieve this?

---

### Post by bobince on 2009-04-29
I don't know if there's any special processing-related trick to sounding like South Park; I think it's just mostly Matt&Trey's voices, probably with some pitch shifting applied.

You can pitch-shift a sample easily enough in eg. Audacity (Effect->Change Pitch).

Doing it ‘live’ is more effort. Usually you'd need to be using Jack, plus Jack-Rack with the LADSPA plugins you want (for example there are pitch-shifters in the swh-plugins LADSPA package). You'd use the Jack Connections window to route microphone input through Jack-Rack and on to whatever program you wanted it to end up in (hopefully one that supports Jack input, otherwise you have to do some tedious messing around with ALSA plugins).

I find the AM Pitchshifter, as well as Stereo reverb, DJ Flanger, Reverse Delay and Ringmod-with-LFO to be fun and effective for real-time voice processing.

---

### Post by higashi on 2009-04-29
Thanks! :]

---

