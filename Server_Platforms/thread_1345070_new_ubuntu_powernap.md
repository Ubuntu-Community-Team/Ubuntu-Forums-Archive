---
title: "new ubuntu powernap?"
date: 2009-12-03
forum: Server Platforms
---

### Post by julianb on 2009-12-03
I have an Ubuntu server (currently running 9.04, but can be upgraded) that spends a substantial amount of time doing nothing, but is powered on nonetheless just in case. This is is not an ideal situation.

I haven't seen any documentation about how to use "powernap" capability that Ubuntu is supposed to have, but I'm interested in learning. I tried google and didn't find anything useful.

Anyone have advice on where to find good info on this topic?

---

### Post by gtfourdreams on 2009-12-12
this is really all that i found: [http://blog.dustinkirkland.com/2009/07/introducing-powernap.html](http://blog.dustinkirkland.com/2009/07/introducing-powernap.html)

i'm running a DL380G3 Proliant server and it doesnt like to go into sleep mode. it will not come out of hibernate mode. i also tried some the cpufreq to throttle the cpu but it looks like the processors dont support it. (xeon gallatins)

---

### Post by Muttley99 on 2009-12-13
There are a few of us on the forum looking at this right now! Powernap does work well on 9.10, you distribution should have pm-suspend as part of the pm-utils pack.

[HTML]sudo apt-get install pm-utils
[/HTML]
Does your bios support WOL and S3?

---

### Post by cllow2020 on 2010-05-23
yes, my server support WOL & S3 in bios, pm-suspend works in terminal type in, but it just can't goto suspend when timeout set in bios..did pm-utils support bios timeout suspend ?

---

