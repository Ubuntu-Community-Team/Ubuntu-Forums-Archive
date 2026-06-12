---
title: "Audio Disc Failing"
date: 2008-05-01
forum: Ubuntu Studio
---

### Post by ions on 2008-05-01
I've burned several audio discs but for some reason a mix album I'm trying to create keeps failing.  I get no errors but when I play the burned disc it's all chirps and pops.

I've made 9 coasters now using Serpentine, Gnomebaker, and Rhythmbox.  

I'm assuming it's a bad mp3 but I'm getting no errors.  Any thoughts?

Up to date Hardy box.

---

### Post by warbread on 2008-05-01
All chirps and pops?  As in, you don't hear anything else? I assume you don't hear the same thing when you play them strait from a media player.  A good test would be to do a live boot, mount your hard drive and burn some mp3s from there.  You may need to install mp3 support.  If that doesn't work, try a Gutsy live boot.  This may be a Hardy bug.

---

### Post by Stochastic on 2008-05-01
I'd be more inclined to suggest manually converting your mp3s to 44100 16-bit wav files (can be done easily in audacity), then try re-burning (as the burning app does this conversion for you).  If it's a bad mp3 then you may be able to dodge this problem, or see it in the wav file you've created.  Also, are you sure the length of the overall cd isn't longer than the disc you're burning it too (maybe trying to burn a 79min disc to a 74 CD etc..).

---

