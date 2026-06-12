---
title: "Delta / Combo Live/Alternate install disk."
date: 2007-10-18
forum: Ubuntu Brainstorm
---

### Post by awilkins on 2007-10-18
My reasoning ; 
The live and alternate disks must share a lot of content. Therefore it could be possible to produce an image that contains both. Or a master image and a delta. Or maybe just a "combo" disk that is larger than a CD but smaller than the sum of the alternate and LiveCD which you could both burn to a DVD to boot as a LiveCD (or a LiveCD generator), and use as an alternate CD for upgrades, or just mount for constructing thumb installs.

My reasons;

I have 2 Ubuntu systems in the house. I distro-upgraded one of them over the network, without really thinking about it. Now I'm facing another 750MB for my other system (I intend to download the alternate installer in case I have to do this again). Plus I keep a LiveCD install on a thumb. Which means yet another 700 MB for the LiveCD.

Ok, it seems a little silly to be arguing about bandwidth in this day and age, but it just seems wasteful.

---

### Post by awilkins on 2007-10-18
Ouch. I just saw the DVD images after a bit of searching. 4.2GB is also a bit steep :)

---

### Post by awilkins on 2007-10-18
Now I've run across the .jigdo links.

The obvious question here is can jigdo construct alternate / live images using the same filebase, saving the differences?

I guess I'm about to find out.

---

### Post by awilkins on 2007-10-18
Hmm, on looking, jigdo isn't going to do very much, because the bulk of it is in the squashfs.

In fact, the squashfs file makes jigdo rather less efficient, because it's always going to have to download 630MB for it. Phooey.

---

### Post by Zdravko on 2007-10-19
Absolutely against it. Keep everything in a 700MB CD!

---

