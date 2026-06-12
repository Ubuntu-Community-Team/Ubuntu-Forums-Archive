---
title: "Hydrogen drum sampler 'noise'"
date: 2009-09-17
forum: Ubuntu Studio
---

### Post by frankwakeman on 2009-09-17
I've found some kind of audio problem with this program Hydrogen, which is like a software drum machine that I'm hoping to create some loops with to use as backing with my home recordings of guitar.

There is some kind of distortion most noticeable I think with the bass drums, through speakers or headphones, even at lowish volumes.  A cracking which I've only occasionally encountered elsewhere with Ubuntu, with the odd video in VLC which then seems to randomly sort itself out.

This is using the HDA Intel Alsa on a Toshiba Equium L40 laptop, 18 months old, and Ubuntu 9.04 (with the same glitch in 8.10).

Thanks in advance.

---

### Post by mr.thraz on 2009-09-17
its probably lantancy.

use jack for low latancey audio work.

---

### Post by frankwakeman on 2009-09-19
Yes, it did turn out to be a latency issue - I should have guessed by the sound, remembering that click from Reason in Windows.  

I've always found Jack to be too much hassle though.  I've been able to export my drum patterns with the OSS driver and then change back to ALSA when moving back to Audacity.

Thanks.

---

