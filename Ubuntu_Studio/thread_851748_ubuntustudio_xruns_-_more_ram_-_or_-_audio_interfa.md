---
title: "ubuntustudio xruns - more ram - or - audio interface?"
date: 2008-07-07
forum: Ubuntu Studio
---

### Post by duojet on 2008-07-07
ok, so I'm running ubuntu studio on an HP dv6790. I'm having trouble getting my latency and xruns down to an acceptable level. i did some mastering today, and noticed that the combination of ardour and JAMin was leaning heavily (60-70%) on the cpu. This, mind you at 44.1 and 256f/p with 23ms latency. I got better numbers with my old 2.8 p4 desk with an audigy card.

I have an Athlon 64 x2 TK-57, 1 gig of ram and for audio, the conexant cx20561 chip (according to lspci).

Obviously, these numbers stink. so what do i do to upgrade? I have about $100 to play with. Do I go nuts and throw in 4gig of ram? Or, do i throw that at a lexicon alpha (or something similar)? Or, split my cash and go with 2 gigs and a 5.1 usb adapter?

ideas?

---

### Post by thorgal on 2008-07-07
hi! what do you need low latency for ? not for mastering I suppose. Jamin is CPU demanding, adding more RAM is not really critical here unless you open tons of applications at the same time. 

The bottleneck is most likely your soundcard. But unless you use your studio box for realtime effects (playing live, etc), low latency is not really required. Ardour compensates and using jamin for mastering definitely makes low latency an unnecessary constraint. 

I have several jackd settings, from ultra low lat to big lat, depending on what I am using my system for. One thing that could help you is at the monitoring level. If you have a h/w that provides you with h/w monitoring, bypassing the CPU altogether, you will have near 0 latency.

Of course, if you do all your FX processing inside ardour, you may need software monitoring. It all depends on your work flow (I usually avoid software FX when I record things, but when I do the mixing, which does not need low latency, I can add some s/w FX).

---

### Post by duojet on 2008-07-07
well, I usually end up using it in one of three ways:

recording live (one channel at a time) with no r/t effects
running hydrogen, zynaddsubfx, and ardour all at the same time
runnning ardour and jackrack, creox or jamin together (not all at once)

Low latency would be nice for playing in hydrogen/zynaddsubfx but I can deal with anything under 20ms.

If I check unlock memory, then I can get down to 10.7ms but, I still end up with about 1 xrun every 10 seconds. And that's jack running by itself. My sound card is pretty "consumer level" so no hardware monitoring.

---

