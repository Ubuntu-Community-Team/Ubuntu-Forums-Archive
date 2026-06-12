---
title: "wine+winepulse"
date: 2010-02-21
forum: Wine
---

### Post by MrMarcus on 2010-02-21
Goodmorning,

I'm looking for a ppa of wine + winepulse integrated.
Explicitly for wine 1.0.1

Thank you,

---

### Post by dino99 on 2010-02-21
latest release is 1.1.39 and it's fine  :P

about winepulse, i think it's not the time to jump into yet:

[https://bugs.launchpad.net/wine/+bug/488981](https://bugs.launchpad.net/wine/+bug/488981)

---

### Post by MrMarcus on 2010-02-21
Hi Dino,

Interesting read.
The issue is, ubuntu uses the pulseaudio sound system. When I use wine (without winepulse) the plugins like OSS, ESOUND ALSA etc. simply doesn't work or stutters/crackles when running wine apps.

For me, and many others, winepulse is -the- solution till Wine implements the OpenAL system.

---

### Post by dino99 on 2010-02-22
yes of course, lot of bug-reports about pulseaudio and alsa not solved yet on Lucid or Karmic. Pulseaudio built into wine is not planned at time, so if it's a big problem for you , the solution is to use the original soft with virtualbox or else, but that need to install MS system too.

---

