---
title: "compiz 'scroll on desktop' &amp; gtk-3.8  scrolling issues"
date: 2013-08-03
forum: Ubuntu Development Version
---

### Post by mc4man on 2013-08-03
Users of Viewport Switcher > Desktop-based Viewport Switching should be aware that there are issues with that plugin & the current 3.8+ gtk that will affect scrolling.
Whether affected depends on use, most obvious will be scrolling in large files with gedit & long package lists in synaptic.

This first was seen with a late committ to gtk in raring, the issue was 'fixed' by reverting the commit in 13.04.
In 13.10 the change is now part of gtk so has returned. 
Initially I couldn't see what was causing this to occur in unity sessions, finally tracked down to the bindings for  Desktop-based Viewport Switching. If they are set scrolling will be affected. (also affects gnome-flashback w/compiz
Current bug on poor scrolling - [lpbug]1184159  [/lpbug]
Also have found that on a laptop if a usb mouse is attached the there is no scrolling at all with that mouse in numerous windows -  [lpbug]1200829 [/lpbug]

While the bug was orig. on gtk it's more likely now only to be fixed in compiz. With the current state of bug fixing in compiz it's quite likely this will not be fixed in 13.10 or anytime in near future. 
In that case, if affected, then you'll need to disable the bindings in Desktop-basedViewport Switching or revert the gtk commit. Seeing as though I use 'scroll on desktop' the later is the only acceptable option here till fixed.
So in meantime will provide gtk packages in ppa with commit reverted, have not yet seen any ill effects of doing so (& was never affected by bug that caused the commit in the first place..
[https://launchpad.net/~mc3man/+archive/test-scroll](https://launchpad.net/~mc3man/+archive/test-scroll)

---

### Post by mc4man on 2013-08-28
I think the probability of this being fixed in compiz is slim to none, same for some inadvertent change in gtk that resolves.
(the later is more likely due to the current state of bug fixing in compiz which is none. Plus the history of compiz 0.9 is that fixes often  tend to break something else anyway

So here will continue to revert until such time that either the revert causes issues or compiz is dead & buried.

---

### Post by grahammechanical on 2013-08-28
I have just been watching the mir feedback session at vUDS. I asked if Compiz will be in 14.10. The answer is No, if all goes well. I had not heard any mention of Compiz in connection with Mir. So I thought I would ask just to confirm what I was kind of expecting.

What we are going to get once 13.10 is released is complaints about Xmir that may be due to the usual Compiz/video driver issues.

Regards.

---

### Post by mc4man on 2013-08-28
It's currently acknowledged that vsync is broken with nouveau & xmir on nv50 chips. (without xmir nv50 is perfect in X & compiz
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1195811](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1195811)

There are 2 possible kernel commits to support vsync at the kernel level for nv50 in nouveau, I've tested them & they work fine. The current downside is that the commits will drop the fps in compiz in half which, while not a critical defect,  isn't good.
When or if these commits show I've no idea, though again don't think there  many or any capable people  available to fix..

(on a side note the commits fix vsync in nv50 in gnome-shell & clutter without the need to set an env for clutter.

---

### Post by mc4man on 2013-10-10
The 2 issues seen when enabling scroll on desktop bindings is being looked at now from the compiz end though it seems to really rest with gtk & xorg
In that case there may not be a solution for 13.10 prior to release.

edit: proposed fix in gtk/xorg works well here, if approved may show post release & in 14.04 which is the real target anyway

---

### Post by mc4man on 2014-02-01
To refresh - 
gtk3 has been fixed so 1 of the 3 bugs is gone (scrolling in an unfocused window

The 2 other bugs that only surface when 'Desktop-based viewport scrolling' bindings are set aren't fixed. A patch submitted to xorg by a gtk dev has been rejected for some [mumbo-jumbo reasons ]("http://lists.x.org/archives/xorg-devel/2013-December/039346.html")so resolution of this is at a roadblock. What will transpire over the next 2 months no clue.

Till such time as fixed a patch xsever-xorg-core for trusty is here, I've found no issue using it & it does fix the 2 scroll on desktop bugs
[https://launchpad.net/~mc3man/+archive/test-scroll](https://launchpad.net/~mc3man/+archive/test-scroll)

---

### Post by mc4man on 2014-04-02
Seems to have finally been fixed in compiz by a persistent dev. Baring any regressions (none yet seen here) should show in compiz update in near future.

Edit: one current regression, no Desktop focus with a window open

---

