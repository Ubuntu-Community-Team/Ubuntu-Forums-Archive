---
title: "Rosegarden with JACK"
date: 2009-04-19
forum: Ubuntu Studio
---

### Post by B4RR13N705 on 2009-04-19
Hi, im running ubuntustudio. I was trying to connect Rosegarden trough JACK, but i can get any sound. I can put notes and everything but i cant listen to them. I connected the Rosegarden Output R & L trough Playback 1 & 2 but nothing. Any idea?

---

### Post by thorgal on 2009-04-20
if you edited a MIDI track, don't forget to add a software synth or patch a MIDI h/w synth for sound output. 

MIDI is not audio, so don't expect to get any audio if the MIDI track sends its MIDI notes nowhere ;)

I helped someone here with qsynth some weeks ago. Maybe you can dig the discussion thread ? 

A suggestion to the forum admins: maybe discussions that turn out to be very useful as they fix common issues, can be made sticky ? I don't keep track of my posts and some of them have turned out quite helpful in some occasions.

---

### Post by kayosiii on 2009-04-20
Midi tracks don't make sounds by default... they just midi signals... 
To do that you need a softsynth, installing and loading zynaddsubfx is a great way to test this -- (this should work automatically if no other midi devices are being routed.) if this fails you will need to route the connection manually. Come back here if you need to do that.

You can also use internal softsynths (purhaps this should be the default) by right clicking the track name and selecting softsynth# you will then be able to configure the softsynth in the bottom of the left hand panel.

---

### Post by B4RR13N705 on 2009-04-20
Yes, i know that, that was exactly what i was doing and rosegarden was function. But suddenly it stoped function, i was using ZynAddSubFX. Maybe i connect something wrong in JACK. Can anybody show me their jack/rosegarden/ZynAddSubFX connection? so i can check if i messed up with something.

---

