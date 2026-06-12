---
title: "Wine Config kills sound"
date: 2010-02-18
forum: Wine
---

### Post by Zubb[RU] on 2010-02-18
Opening Wine Config kills sound on the system. Any ideas why this can happen?

Happens only if some sound is being played then opening wine config. Otherwise works fine. Not much of the problem this way, realy.

---

### Post by dino99 on 2010-02-18
what wine release ? (latest in wine-ppa is 1.1.38 and work fine)

what sound driver is used into wine ?
have you sound problem outside wine ?

Something in wine log ?

Try with other sound driver into wine.

---

### Post by Zubb[RU] on 2010-02-18
wine is 1.1.38 

Q. what sound driver is used into wine ? 
A. OSS. Tried changing to other ones - this doesn't affect the bug.

Q. have you sound problem outside wine ? 
A. nope


If no sound is playing when wine is started everything functions normally.

---

### Post by aggroredbeard on 2010-02-19
same problem over here.

Tryed so specify the mixer (asoundconfig-gtk) to pulse audio bzw SB.
Wine version 1.1.38
Karmic Koala Ubuntu,
A onboard soundcard.

I tried Alsa, OSS and Jack. No change. Sometimes it works with games like wow (have to start wow first then musik or any other Pulse sound.
Whene the Pulse doesnt make a sound anymore, I kill all programs wich trying to acces the soundserver, waiting a secon, an starting the software one more. Most Time its working, but the wine Programs always making problems.

any useable workaround here?

---

