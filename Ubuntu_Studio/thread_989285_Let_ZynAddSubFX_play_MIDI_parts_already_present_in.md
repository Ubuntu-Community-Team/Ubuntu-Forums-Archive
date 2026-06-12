---
title: "Let ZynAddSubFX play MIDI parts already present in Rosegarden"
date: 2008-11-21
forum: Ubuntu Studio
---

### Post by groundnut on 2008-11-21
I copied some MIDI parts from Cubase to Rosegarden.
Now I want to use the standalone softsynth ZynAddSubFX to play these MIDI parts.

How can I activate/select ZynAddSubFX in Rosegarden?

---

### Post by markbuntu on 2008-11-24
In patchage you can hook the Rosegarden MIDI channels into ZynAddSubFX and the ZynAddSubFZ out to wherever, system out, ardour. For MIDI drum tracks you can do the same with Hydrogen. It's quick and easy. You could also use QSynth.

---

### Post by groundnut on 2008-11-26
I installed patchage and was able to drive ZynAddSubFX from Rosegarden via patchage.
My next question is: how can I do the same multitimbrally? So how can I use 2 different sounds from ZynAddSubFX at 2 different MIDI channels?

P.S.: When would I record audio in Ardour instead of in Rosegarden?

---

### Post by paulmerchant on 2008-11-26
ZynAddSubFX is multitimbral. On the main screen, simply switch to and then enable another part (the part changing is right above or next to the volume, depending on if you are using the beginner or advanced interface). ZynAddSubFX will default this second part to midi channel 2 so everything Rosegarden sends on channel 2 will play this second part.

You second question really depends on your needs and comfort levels. Using Ardour will introduce a new layer of complexity, but then I think it's a good idea to learn Ardour. In fact, if you have even a small annoyance with Rosegarden's audio editing, spend a little time to learn Ardour.

---

