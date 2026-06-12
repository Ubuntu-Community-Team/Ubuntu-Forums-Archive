---
title: "insufficient ram error in virtualbox"
date: 2011-09-14
forum: Virtualisation
---

### Post by jimmybarcelona on 2011-09-14
I installed Virtualbox (version 4.1.2) solely so I could play some old windows games, namely Command and Conquer Red Alert 2. Whenever I try to run the installer, the system throws the error "Insufficient RAM available. A necessary component could not be created."

I'm running 32bit WinXP. I have virtualbox allocating 107 megs of video memory, and 850 to RAM. That should be more than enough to run Red Alert 2. I installed the current Guest Additions in XP safe mode, with 3D support enabled, and have 3D acceleration enabled in Virtualbox options.

What am I missing?

---

### Post by haqking on 2011-09-14
> **jimmybarcelona said:**
> I installed Virtualbox (version 4.1.2) solely so I could play some old windows games, namely Command and Conquer Red Alert 2. Whenever I try to run the installer, the system throws the error "Insufficient RAM available. A necessary component could not be created."

I'm running 32bit WinXP. I have virtualbox allocating 107 megs of video memory, and 850 to RAM. That should be more than enough to run Red Alert 2. I installed the current Guest Additions in XP safe mode, with 3D support enabled, and have 3D acceleration enabled in Virtualbox options.

What am I missing?


how much ram does your host have ?

107 of vid mem seems a little steep, though i dont play games in a VM.

To be honest for games you are better running natively from a dual boot perhaps.

However i would assign more system memory and possibly less grpahics memory.

How much memory does your host graphics have ?

---

### Post by jimmybarcelona on 2011-09-14
host has 2 gig ram, and a 256 meg nvidia card.i'll dial off the video memory and turn up the ram a bit, though  red alert 2 only requires 64 meg of ram so i figured over 800 would be fine..

---

### Post by haqking on 2011-09-14
> **jimmybarcelona said:**
> host has 2 gig ram, and a 256 meg nvidia card.i'll dial off the video memory and turn up the ram a bit, though  red alert 2 only requires 64 meg of ram so i figured over 800 would be fine..


yeah if i was you i would play with the settings a little. I never assign the graphics over 32,  but to be fair i dont play games in them.

And never assign more than twice your host ram though i see you never.

and remember not all games are gonna play on virtualised hardware like they do in a native environment ;-)

---

### Post by jimmybarcelona on 2011-09-14
i'm okay with it not running as well as in a native environment, but i at least want to get it to install. I'll post back if I can get it working.

---

