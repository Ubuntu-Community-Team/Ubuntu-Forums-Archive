---
title: "Game freezes every 6 seconds"
date: 2009-07-25
forum: Wine
---

### Post by xZachtmx on 2009-07-25
Ok im playing a game i used to play on windows called starport galactic empires.  ([www.starportgame.com]("http://www.starportgame.com")) the game runs amazingly in wine 1.0.1 and the framerate is even better than when it was in windows.  But every 6 or so seconds the game freezes for a second.  I was wondering if there was a way to configure wine to get rid of this... or maybe something else?

---

### Post by NightMKoder on 2009-07-25
Try the latest wine 1.1.26 (read sticky on top on how to get it).

---

### Post by xZachtmx on 2009-07-25
i know its the latest but it isnt the latest stble version... it dosent work for starport... well it does just fps is 1 per second.. i would just like to know how if possible to change wine to work for me?

---

### Post by NightMKoder on 2009-07-25
The whole stable/unstable thing is not very descriptive. Wine is itself never stable, it's just that 1.0 was the first actual release, after which, wine went into the 1.1.0 series.

What video card do you have? It's usually a graphics card issue. Also post a log with the newer wine.

---

### Post by rocky5051 on 2009-07-26
> **NightMKoder said:**
> The whole stable/unstable thing is not very descriptive. Wine is itself never stable, it's just that 1.0 was the first actual release, after which, wine went into the 1.1.0 series.

I beg the differ. The current stable branch is a version of WINE that was cleared of many regressions and cleaned up a bit during the code freeze leading up to 1.0. Thus being more stable than, say, the most recent GIT version from their servers. While it may never be fully featureful, what was there would be expected to be fairly stable.

But anyway, it might pay to visit the AppDB and search for your game to see if anyone has encountered the bug as well and found a fix. :)

---

### Post by philcamlin on 2009-07-26
> **xZachtmx said:**
> Ok im playing a game i used to play on windows called starport galactic empires.  ([www.starportgame.com]("http://www.starportgame.com")) the game runs amazingly in wine 1.0.1 and the framerate is even better than when it was in windows.  But every 6 or so seconds the game freezes for a second.  I was wondering if there was a way to configure wine to get rid of this... or maybe something else?

id upgrade to the new wine

---

### Post by xZachtmx on 2009-07-26
hmm i dont know... when i upgraded to 1.1.23 i got a framerate of 1 per 6 seconds :(  thanks for your help ill keep trying

---

### Post by rocky5051 on 2009-07-26
Well, if there is nothing available from the AppDB to assist you in fixing the problem, and there is no reason that you require the newer version of WINE, I would suggest uninstalling the new version and installing the stable version (1.0.1) instead to resolve the issue.

The only reason you should need to upgrade is when something has been implemented and shown working for an application you want to use that was preventing you from using said app.

---

### Post by xZachtmx on 2009-07-26
Well i alredy have 1.0.1 . it is working fine as i said its just the lag spikes every 6 seconds.  Weird

---

### Post by Yeeha on 2009-07-26
> **xZachtmx said:**
> hmm i dont know... when i upgraded to 1.1.23 i got a framerate of 1 per 6 seconds :(  thanks for your help ill keep trying

in 1.1.23 they changed from pbuffer to fbo by default which caused problems to some so u can try to reverse it from wine registry.
Also making wine more important process may help too, fallout 1 or 2 was kind of slowish for me and i put priority -10 and then was fine.

---

### Post by NightMKoder on 2009-07-26
My point was to say, that calling wine stable at any point does not really make sense. Perhaps the only reason the game works for you is because something was not implemented in 1.0.1 and wine just ignored it.

But yes, if you're on an ATI card especially, take the offscreenrenderingmode suggestion.

It's always a good idea to have your program work on the latest wine since, well, nobody really supports the stable version.

---

