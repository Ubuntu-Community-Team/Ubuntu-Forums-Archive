---
title: "Finding RF signals"
date: 2006-02-13
forum: Server Platforms
---

### Post by seekyrr on 2006-02-13
When doing site surveys, what tools do you guys use to find the rogue AP?

I can detect with kismet, Wellenieter or a wl scan, but I am having finding exactly where they are.

I don't have GPS right now..which I assume would solve the problem, but I was wondering if there is a way to find them without.

Thanks

Seek

---

### Post by robert_pectol on 2006-02-14
Without a GPS receiver and software to correlate the access point's signal strength to various locations, you'll have to manually triangulate on its signal.  You'd probably proceed by using a directional antenna and taking several relative signal strength measurements from a variety of locations.  Once you have several "good" bearings, map out where they all intersect and proceed with a localized search in that vicinity.  That may also require the use of a variable attenuator as you "home in" on the access point.  DF'ing (direction finding) an RF signal is somewhat of an art that takes some practice to get good at.

---

