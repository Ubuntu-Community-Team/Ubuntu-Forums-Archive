---
title: "Launcher Bar icons tooltips sometimes get stuck on screen"
date: 2012-02-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-02-01
My Launcher Bar is set to never hide. Sometimes when I accidentally hover over some Luncher Icon while moving the mouse, the tooltip shows and stays stuck in the screen. Then the only way to make it disappear is to launch the icon for that tooltip (clicking other icon or anywhere else won't do). It's starting to become more frequent and annoying. 
Anyone confirms?

Regards,
Effenberg

---

### Post by VMC on 2012-02-01
Interesting. Mine is just the opposite. Its set to auto-hide and only reveal at the top-left. That rarely works.

 I move the mouse around the top-left nothing happens, or it reveals sometimes. 

I'm unsure at the moment if its a bug or something I'm doing wrong.

---

### Post by mc4man on 2012-02-01
> **VMC said:**
> Interesting. Mine is just the opposite. Its set to auto-hide and only reveal at the top-left. That rarely works.

 I move the mouse around the top-left nothing happens, or it reveals sometimes. 

I'm unsure at the moment if its a bug or something I'm doing wrong.

If you are using top left reveal in **unity-5.0 or earlier** you need to do a semi-specific mouse movement

Something like this - 
move cursor to top left corner, **don't** come in exactly centered.
Then pull cursor down the far left edge, once it clears the panel area & gets into the launcher area the launcher will show.
Also make sure your reveal delay in the unity plugin > experimental isn't set to a high value, for top left only you can make it the min if desired

As of unity-5.2 this, ^, becomes moot. Reveal will be based on left edge 'pressure'

As far as orphaned tooltips, that's been going on since natty. Not sure I've ever found any single reason why. (currently haven't seen

---

