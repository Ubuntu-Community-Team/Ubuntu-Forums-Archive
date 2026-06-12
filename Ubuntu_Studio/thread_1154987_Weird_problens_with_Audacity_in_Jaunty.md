---
title: "Weird problens with Audacity in Jaunty"
date: 2009-05-10
forum: Ubuntu Studio
---

### Post by vootpig on 2009-05-10
I was using Audacity to put together a few tracks of recorded music, so, I imported the wav files and was adjusting some stuff, doing some edits like generating silence over background noise, amplifying quiet bits, simple things like that. Then, out of nowhere, when I pressed the play button, the playback was only static, and when I pressed the stop button the program crashed.

This happens to me now literally every time I run the program, regardless of what my actions are. Sometimes if I stop the playback right after it spits static, I can wait a minute and it will return to normal. But, invariably, the program crashes within 10 minutes, sometimes within 1 minute of starting the program.

I tried a re-install, and eventually even did a "complete removal" of Audacity and its data files and then performed a fresh install, but the same problem arises.

I can't imagine that the wav files are the culprit, because I've worked with the same kind of files (even recorded by the same device) in the past and never had this problem.

Can anyone lend me a hand? :(

---

### Post by sgx on 2009-05-12
Hi, it might be an older audacity will work better, as the kinks are removed from the newest. Also the dependancies, and window-manager may
be involved, maybe try updating to the latest kde3 or gnome, xfce etc etc
. Is there plenty disk space for the audacity temp project files? Maybe lots of edits generate lots of them, and if that partition is nearly full, it might act up. Some new audacity versions work with jackd, but don't show it in the qjackctl gui, if you have such a version, pulse-audio might even be involved, lots of threads here about that jackd Vs pulse-audio conflict.
I woulld do a new linux install with the newest distro that you like. When fre software goes bonkers, its often faster to work from a clean slate, than to find someone with the inside info. The audacity devs would probably appreciate a bud-report since you are digging into theit features. Cheers

---

