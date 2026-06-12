---
title: "volume weirdness"
date: 2009-09-23
forum: System76 Support
---

### Post by jmwink on 2009-09-23
[gazu1]

I've been having this issue for the last week or so, and sort of thought I was going crazy:

I boot up, get the nice start-up noise, and everything sounds nice. I go to open VLC and play some music, and the volume immediately becomes muted, red "x" at the bottom of the little speaker icon in the tray. I have to open volume control to unmute, and then pull the slider up. Once I do this once, everything is fine, but it's like a little ritual on first boot. I've tried with every audio program I can (Rhythmbox, Exaile, Quod Libet, Gmusicbrowser) and they all do the same thing. Can't figure this one out. 

I wish I had been paying more attention to see if there was an update to pulse-audio or something that occasioned this problem, but as I said, I sort of thought I was going crazy and imagining things.

Any ideas?

---

### Post by jordansc on 2009-09-24
I found this in the Ubuntu forums:

[http://ubuntuforums.org/showthread.php?t=1145603](http://ubuntuforums.org/showthread.php?t=1145603)

> **Cybie257 said:**
> This has been solved. 

Reading through many bug articles, apparently something 'un-ticks' the check-box for:

     Audio settings management (alsa-utils)

within the Services Settings. (IE: System->Administration->Services)

Weird. Never had that problem before. 

But, it's fixed. :guitar:

-Cybie


Hope this helps.

---

### Post by jmwink on 2009-09-24
Thanks!

---

