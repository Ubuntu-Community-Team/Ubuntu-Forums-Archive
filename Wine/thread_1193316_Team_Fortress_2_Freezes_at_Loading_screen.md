---
title: "Team Fortress 2 Freezes at Loading screen"
date: 2009-06-21
forum: Wine
---

### Post by Beezleray on 2009-06-21
Hello, I've been running Steam + TF2 for a while now, but about a week ago every time I'd go to play it the game would freeze at the loading screen in the beginning. 

It loads steam fine, loads the Valve intro and then the game freezes after that, I've looked around and can't seem to find a fix, can anyone help me on this?

Thanks!

---

### Post by NightMKoder on 2009-06-21
Is that by any chance when you updated to wine 1.1.23? And do you have an ATI card?

Switch your offscreenrenderingmode to backbuffer.

EDIT: Holy crap I'm a moron. Switch it to backbuffer***. [http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

---

### Post by Beezleray on 2009-06-21
> **NightMKoder said:**
> Is that by any chance when you updated to wine 1.1.23? And do you have an ATI card?

Sorry, I forgot to list this, I'm running Wine 1.1.20 with Nvidia drivers.

> **NightMKoder said:**
> Switch your offscreenrenderingmode to fbo.

I think I remember doing this, but how do I check just to make sure.

---

### Post by NightMKoder on 2009-06-21
[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys) and check my earlier post because I meant to say backbuffer, not fbo... fbo is what crashes ati cards.

---

