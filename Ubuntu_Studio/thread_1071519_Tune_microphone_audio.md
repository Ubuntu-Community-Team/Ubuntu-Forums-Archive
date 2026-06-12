---
title: "Tune microphone audio?"
date: 2009-02-16
forum: Ubuntu Studio
---

### Post by Flames on 2009-02-16
This isn't really a problem, but I'm trying to find out 
if its possible to change the pitch of audio coming from the  microphone or LineIn input in real time. I'm not quite sure how to go about this (whether there is a setting or some software). 
if anyone could tell me, that would be appreciated.
:guitar:

---

### Post by Stochastic on 2009-02-16
Jack Rack is the best application for this, just do ```
sudo apt-get install jack-rack ubuntustudio-audio-plugins
```
then you should have a variety of pitch-shifter LADSPA plugins to use on your mic input.

More elaborate versions can be constructed with a little intermediate-to-advanced pure-data programming, but that's a little complex to explain right now.

---

