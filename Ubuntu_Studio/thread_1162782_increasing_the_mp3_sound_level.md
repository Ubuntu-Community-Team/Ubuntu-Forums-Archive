---
title: "increasing the mp3 sound level"
date: 2009-05-18
forum: Ubuntu Studio
---

### Post by tiatlon on 2009-05-18
I have a mp3 player which has a very low maximum sound volume level, and there are some audio books which also have very low volume and I can't listen to those files on my mp3 player. Is there a soft in Ubuntu which can increase sound volume level of a group of mp3 files? (so far I've been reading only about normalizing level, but haven't found anything about increasing sound volume level)

Thank you in advance.

---

### Post by luctor on 2009-05-18
You'll need a compressor for that.

Normalising does max out the amplitude of a wave form, this does increase the volume, but if there's a lot of dynamics (soft parts and loud parts) in a audio file then the soft parts will stay relatively soft.

A compressor pumps up de volume of the soft parts and limits the loud parts of the audio file, thus levelling out the dynamics.

Sox (a command line sound editor) has a compressor effect call compand

Audacity also has as a compressor effect.

---

