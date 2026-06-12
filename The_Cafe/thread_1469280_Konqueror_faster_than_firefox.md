---
title: "Konqueror faster than firefox?"
date: 2010-05-02
forum: The Cafe
---

### Post by jerenept on 2010-05-02
I just installed konqueror on ubuntu 10.04 LTS and noticed how much faster it seemed to be than firefox. Does anyone have any benchmarks or so on to prove or disprove this?

---

### Post by aysiu on 2010-05-02
After a certain point, speed doesn't matter. But, yes, Konqueror is faster than Firefox.

---

### Post by Kadai on 2010-05-02
I did have a similar issue.
But, I have seen that the name resolution for firefox in Kubuntu 10.04 is pretty slower than anything else in the system.

For example, to load google.com, in konqueror it takes almost zero seconds, but in firefox, it can take around 10 seconds or more just for resolution.

I'm not sure if this issue is related to only this package or certain configurations, because I have not seen any bug or report around.

Nevermind, found the reason at: [http://ubuntuforums.org/showthread.php?t=1467763&highlight=firefox+dns](http://ubuntuforums.org/showthread.php?t=1467763&highlight=firefox+dns)

---

### Post by init1 on 2010-05-02
Probably. It uses Webkit, the same rendering engine as Chrome and Safari. On a low-spec computer, the extra speed does make a difference. On a faster computer, you may not notice any difference.

---

### Post by antenna on 2010-05-02
I imagine it is, I switched to Epiphany lately and it's also noticeably faster than Firefox.

---

### Post by nortexoid on 2010-06-21
Firefox should be faster than Konqueror *UNLESS* you're using the "--graphicssystem raster" option with the latest Qt (and some earlier versions) and intel graphics driver stack. Java is still faster in Firefox but using raster for Konqueror makes general 2D stuff including fullscreen flash a lot smoother and faster than firefox, which isn't built on qt and hence can't use the raster backend. Theoretically raster should be slower than native and opengl should be faster than both, but if you're using an intel graphics driver, most likely opengl won't be usable and raster will be way faster than native.

In any case, I've switched to Konqueror just because raster makes things so much smoother, plus the integration with KDE is a bonus. Unfortunately Firefox is still needed for certain web sites.

---

