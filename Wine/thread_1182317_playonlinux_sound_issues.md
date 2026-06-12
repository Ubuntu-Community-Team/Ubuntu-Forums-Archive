---
title: "playonlinux sound issues"
date: 2009-06-08
forum: Wine
---

### Post by ForMar on 2009-06-08
I have gotten the sims 3 to run and stay open, but Im having issues with audio. This is the first and only game that I have installed so I have no way of telling if this is a general issue or a specific one with this game. But im pretty sure that its an over all wine problem. My knowledge with linux is low so please instruct accordingly.

To the problem:

I have eDimensional AudioFX Pro 5.1 Force Feedback USB Gaming Headset ( awful headset) that uses Alsa mixer. Listed in ubuntu as c-media usb headset. It works as should in ubuntu but when I launch the sims 3 it has absolutely no sound. Ill be monitoring this and I will be happy to post any info that is required to help solve this problem.

Some solutions I have attempted:
-I attempted to killall pulseaudio but it seems to just relaunch the min I attempted to start the game
-I attempted to use padsp ( no idea what it does tbh) but was instructed to put that before running wine in terminal. The problem being that I use playonlinux so I dont know how to access the config file it specifically makes for the game.

Please not this seems to be a wine issue not a "POL" issue

I appreciate your time in reading this and helping me out

Thanks,
Anthony

---

### Post by Propeng on 2009-07-03
I have this problem too. Sound works fine in Wine, but not in POL (I know they are the same).
I tried testing sound by using Wine configuration and I get this:
```
ERROR: Audio testing failed!
```

---

### Post by NightMKoder on 2009-07-03
use pasuspender to launch without pulseaudio.

---

### Post by Th3_uN1Qu3 on 2009-07-03
Or remove the dreaded PulseAudio entirely... It doesn't play nice with anything.

---

### Post by Propeng on 2009-07-04
I don't use PulseAudio. I guess the problem is in the compiled WINE in POL.
(I sometimes get this problem on WINE itself)

---

