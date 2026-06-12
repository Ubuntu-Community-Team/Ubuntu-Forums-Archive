---
title: "Dell laptop+firepod: Which distro to try next?"
date: 2009-06-29
forum: Ubuntu Studio
---

### Post by trulan on 2009-06-29
I'd like some input on where to go next:

The laptop is a Dell Inspiron E1505.  It has a built-in Ricoh firewire chip.  (Presonus says this is bad).  So far I have tried:

Windows XP Media Center with built-in firewire port. (bad, bad, bad)  Also tried with a TI-based firewire express card (light turns blue but nothing works at all).

Ubuntu Studio 9.04 with TI-based express card. (Jack won't connect)  Then tried with built-in firewire port.  Jack connects, works sometimes for a few minutes, but system always freezes, requiring a hard reset.  Another user in another thread observed the same behavior and fixed it with an older kernel.

64studio 2.1 with built-in firewire.  This will work sometimes.  I have had Jack running for over an hour continuously, but sometimes I only get a few minutes before it halts with a 'zombified' error.  I would like to try running ffado instead of freebob on this setup but upgrading this seems pretty complicated and so far eludes me.

So I want to know what I should try next:  64studio 3.0 beta or Ubuntu Studio Hardy?  Which will give me the best shot at a kernel that is stable on this machine and be able to run ffado?

---

### Post by trulan on 2009-07-01
I decided to go with Ubuntu Studio 8.04.  Initially, I experienced exactly the same behavior as on 64 studio 2.1.  I fixed it by doing this:

Enable khashayar PPA as described here:
[http://ardour.org/node/2660](http://ardour.org/node/2660)
(this PPA says it is being disabled, but it seems to still work.)

In Synaptic:
1. Install libffado
2. Upgrade Jack
3. Upgrade Ardour

Restart computer.

Performance is much improved.  Jack can run at lower buffering settings than before, and survives xruns instead of crashing with a 'zombified' error.  It also starts properly every time, whereas it used to take three or four tries.  And when it does crash (I was really pushing the buffering settings and running several programs), the light turns red on the firepod, and it can be re-started.  Before the light would stay blue, and I either had to switch the firepod off or unplug the firewire cable before I could re-start.

So,I need to give it a real-life workout, but I think this problem is solved.

---

### Post by trulan on 2009-07-04
Let it be known that I am officially happy!!

This laptop was bought three years ago, along with a firepod, for recording purposes.  It never worked.  We had completely given up on it as a waste of money, and were actually carting my desktop around because it at least worked.  No more of that!!

It is now officially fixed, working, stable, can you tell I am excited?  Ubuntu rules!!

Actually, Jack, Jack Rack, Patchage, and Ardour rule.  This stuff is just amazing.

BTW, according to a post by Stochastic, 64studio 3.0 is based on the same kernel as Ubuntu Studio Hardy, so that would have worked as well.  But with it running this well I'm staying put.

---

