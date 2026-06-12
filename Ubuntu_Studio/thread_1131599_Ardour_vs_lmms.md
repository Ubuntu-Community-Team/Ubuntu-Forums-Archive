---
title: "Ardour vs lmms"
date: 2009-04-21
forum: Ubuntu Studio
---

### Post by elliotn on 2009-04-21
Which is better

---

### Post by kayosiii on 2009-04-21
Which is better - a ferrari or a truck?
Depends on what you are doing....

If you tend to record most of your music from outside sources and work at a track a time then Ardour will suite your workflow more.

If you tend to build compositions out of looping patterns then lmms will fit you better.

Ardour I would consider the more mature and stable of the two offerings but they are designed to compose music in different ways.

---

### Post by Stochastic on 2009-04-21
Kayosii is right on.  The only thing I could add is a closer analogy that may shed light on the differences:
What's better Pro Tools or Fruity Loops?

(please give this analogy a similar artistic license as the truck/ferrari one - no flaming or foss/commercial war)

---

### Post by nickleus on 2009-08-06
correct me if i'm wrong, but the ardour2 in the repos doesn't support midi, but lmms seems to (i haven't tried it out, i just installed it)

---

### Post by Stochastic on 2009-08-06
You're quite right, midi doesn't land in Ardour until version 3 (which hasn't been released yet, but is supposedly coming very soon).

---

### Post by sgx on 2009-08-07
> **nickleus said:**
> correct me if i'm wrong, but the ardour2 in the repos doesn't support midi, but lmms seems to (i haven't tried it out, i just installed it)
Thats pretty likely, so you can use qjackctl to connect LMMS output to Ardour input, and use the best features of both. If you have wine/wineasio installed, LMMS will use it to enable vst plugin usage from LMMS, not as stable as using Reaper, but getting better with each release.
Fst and dssi-vsthost can also use qjackctl for connections and host single vst plugins. DiscoDSP has now open-sourced the great Highlife sampler, and it will also host vsts in linux quite nicely, among its many excellent features! And they also have a great linux native synth, Discovery Pro, that ships with a huge and excellent library of presets, created over the last few years. Of course, everything can be routed to rakarrack and Creox, for massive multi-fx, spoiled for audio riches, and haven't even opened up Zynaddsubfx yet!

Cheers, its the weekend! :D

---

