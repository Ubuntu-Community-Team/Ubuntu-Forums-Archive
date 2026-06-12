---
title: "set up webcam server"
date: 2010-11-28
forum: Server Platforms
---

### Post by philipballew on 2010-11-28
i need to set up my laptop to stream its webcam to me wherever i am and can view what is going on from there. this is going to be the sole purpose of this computer, how would i do this? the laptop has a ppc processor

---

### Post by HermanAB on 2010-11-29
Motion or Zoneminder.

---

### Post by philipballew on 2010-11-29
does this run on ppc though? i was unaware it did

---

### Post by HermanAB on 2010-11-29
Check the Debian PPC repos, otherwise compile from source.

---

### Post by philipballew on 2010-12-05
so now how will i compile from sourse and run in ubuntu server edition? i assume its desgined to run with s gui?

---

### Post by SquALeD on 2010-12-09
You said s GUI. I assume you meant a GUI?

As Herman said the 2 top ones are motion and zoneminder, both are CLI. I reccomend zoneminder, the learning curve is vertical but once you master it it runs rock solid and does stuff that CCTV systems costing thousands of $$ do.

If you're using 10.04 its in the repo -  sudo app get-install zoneminder will install everything you need.

HTH

---

