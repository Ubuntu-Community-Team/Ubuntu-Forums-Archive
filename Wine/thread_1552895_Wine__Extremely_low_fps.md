---
title: "Wine / Extremely low fps"
date: 2010-08-14
forum: Wine
---

### Post by Tzah on 2010-08-14
So far, every game I've tried to run in Wine runs with drastically low (~10fps) performance. Warcraft 3 was completely unplayable, even Starcraft ran like it was on a 50mhz processor from 25 years ago, clogged with hair and dust and powered by a wooden mouse wheel. 

This is a pretty old (1.2ghz Athlon, 1 gig RAM, Geforce FX 5200) PC, but surely games as old as Starcraft shouldn't be stuttering along like a geriatric with a zimmer frame? Could it be something amiss in the Wine config or otherwise? For comparison, 'Hacker Evolution' through wine ran at something like 8fps, but native Linux ran at more like 60. 

Ubuntu distro is 10.4 and the wine distro is 1.1.42.

---

### Post by cogadh on 2010-08-14
Well, there will always be some performance loss when comparing a game run in Windows to a game run through Wine. The same is also true when comparing a Linux native game to a Windows version run in Wine. There really is nothing to be done about it, but it does sound like you are getting performance well below what would be expected, even with Wine getting in the way of performance. 

The first thing I would do is update to a more current version of Wine (1.1.42 is a few months out of date), either the 1.2 stable version or the current 1.3.X unstable. Generally speaking, the unstable versions of Wine are better for gaming, though they can sometimes have bugs not present in the stable version. You should be able to get 1.2 through the Ubuntu repositories, directions for getting 1.3.X can be found [here]("http://www.winehq.org/download/deb").

---

