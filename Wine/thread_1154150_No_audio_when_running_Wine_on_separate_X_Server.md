---
title: "No audio when running Wine on separate X Server"
date: 2009-05-09
forum: Wine
---

### Post by stratman1988 on 2009-05-09
I just did a fresh install of Jaunty Jackalope moving from Hardy Heron and use the attached script to run fullscreen games on Wine. This worked fine for in Hardy but in Jaunty when I run the script, ALSA fails with this line.```
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: Permission denied
```
I've attached debug output from Wine
I've tried using OSS and JACK for wine, as well as killing my main desktop to make sure is wasn't hogging all the sound resources.  Has there been some change in the way audio or the X server is handled in Jaunty that is causing the audio to fail I initialise a new server??

---

### Post by jludeman on 2010-05-01
Anybody ever solve this problem?

I have the exact same problem.

I just "upgraded" to Jaunty from Hardy and this one of several things that worked under hardy and is broken under jaunty.

---

### Post by stratman1988 on 2010-05-01
Nope, still a problem.  I think it's because they've changed the way X server fires up from Jaunty on.

---

