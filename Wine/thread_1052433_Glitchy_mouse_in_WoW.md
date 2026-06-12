---
title: "Glitchy mouse in WoW"
date: 2009-01-27
forum: Wine
---

### Post by Valok on 2009-01-27
Over the past few weeks I've started running into some mouse problems.  Randomly my mouse will not show up on some parts of the screen.  Like for instance a lot of times it won't show up anywhere on the top 1/4 of the screen for a couple minutes at a time.

Also I often times run by pushing down the two mouse buttons, but for some reason my left mouse button is freaking out as of late.  It won't stay clicked, or it randomly double clicks quite often, and its very irritating.

---

### Post by Ameneon on 2009-01-28
Don't have a solution for you but I've noticed at least the disappearing mouse glitch as well, seems to have appeared after the upgrade (not the one today but the one a few days back). Not heard my gf complain so I'm guessing it's wine/linux only.

---

### Post by Valok on 2009-01-28
Ok, I've found the problem.  What happens is that when you mouse over something too far in the distance, the mouse goes away.  This is a WoW bug, not a wine bug.  The fix for it right now is enabling a feature that doens't exist for openGL.

So for now, set your view distance to the lowest, or next to lowest and your mouse will be back working fine.

---

### Post by Zoquara on 2009-01-28
I found this on the WoW tech support forums....

> It seems the problem only happens when the max draw distance clip is set to 500 or above. The following farclip command will fix the issue;

/console farclip 499

It's a poor solution, but it works

Just type in or cut 'n paste the /console command in-game. It worked for me like a charm.

---

### Post by Ameneon on 2009-01-29
Hm, interesting.

Thanks a ton, that worked just fine :)

Makes sense too, my gf is playing on a weaker GPU and so doesn't have the view distance set to max.

---

### Post by mrfr0g on 2009-02-11
*bump*

Thanks this worked great for me too

---

### Post by Mmmbopdowedop on 2009-02-12
For those that have done this and not read the patch notes, this bug no longer exists in the WoW client as of 11/02.

So there's no need to lower your distance anymore. :)

Just throwing that out there. :)

---

