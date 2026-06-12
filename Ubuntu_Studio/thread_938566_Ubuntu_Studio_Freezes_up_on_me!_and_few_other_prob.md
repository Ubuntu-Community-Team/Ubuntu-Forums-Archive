---
title: "Ubuntu Studio Freezes up on me!? and few other problems"
date: 2008-10-05
forum: Ubuntu Studio
---

### Post by XVampireX on 2008-10-05
Hi, I'm having some major problems with ubuntu studio, I installed it, the 32bit version, with nv driver things seem to work here and there but after some time, it just freezes up, at first it looks like just some apps are frozen but after I do something, even a console command (I.E: sudo killall gdm) it just completely freezes. For example I installed lastfm, put it on some artist overnight to hear while I'm sleeping, it started okey but then things just really screwed up when I woke up.

Another major problem is with nvidia drivers, 177.78 that I tried (the ones in the repositories are just too old) installing, which installs fine but causes even more problems with freezing, and after a restart doesn't let me go on gdm at all says I have some problems with the xorg drivers.

Another problem was with my sound cards, sometimes my audiophile 2496 card just either crashes or doesn't load at all on boot. And because of that I couldn't get jack to run with it.

I had a few more problems but that's for later, after the major problems get fixed...

If there's any chance anyone could help me, I thought 8.04.1 was supposed to be stable, no?

And yeah, I installed it from the alternative CD.

Thanks.

---

### Post by XVampireX on 2008-10-06
How can these posts go without any answer? I've seen other people asking questions about some really difficult problems and they never got any reply...

So much for support...

---

### Post by rybaxs on 2008-10-06
my Ubuntu Studio Freezes up in the middle of installation? does anybody know what are the specs for Ubuntu Studio? Some of my friend install Ubuntu Studio at there Laptop... 

try 8.04...

---

### Post by Bungo Pony on 2008-10-06
Mine used to randomly freeze up on me for about 20 seconds at a time. There were two ways for me to fix it...

1) Turn off Compiz Fusion.
2) Get more RAM

After I installed more RAM (I had only 512K, I now have 2G) the freezing problem went away.

If you're getting the random freezing, you could try installing conky and you'll be able to see what's either gobbling up your ram or CPU power. Typing dmesg in a terminal may also tell you what's going on with your system.

---

### Post by snowpine on 2008-10-06
I had nothing but trouble with Ubuntu Studio's "real time kernel". I got rid of it and now I use the regular (non-rt) kernel exclusively. No more freezing up.

---

