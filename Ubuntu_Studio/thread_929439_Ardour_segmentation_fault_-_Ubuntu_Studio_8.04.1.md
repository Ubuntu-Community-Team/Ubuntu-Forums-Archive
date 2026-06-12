---
title: "Ardour segmentation fault - Ubuntu Studio 8.04.1"
date: 2008-09-25
forum: Ubuntu Studio
---

### Post by djpenguin on 2008-09-25
I just did a fresh install of Ubuntu Studio 8.04.1, and every time I try to start Ardour, it suffers a segmentation fault right after attempting to load the session.

I've tried both the standard and -i686 branches that are in the repositories, and I downloaded the Ardour 2.5 deb from getdeb.net too.  They all suffer the same problem in the same place.  JACK seems to be working just fine, so I have no idea what's going wrong here.

Any thoughts?

---

### Post by Stochastic on 2008-09-25
Segmentation faults are nasty bugs that should be filed on launchpad.  Particularly if it's a fresh install - things should be working perfectly.  The devs should have better answers & they will respond to a launchpad bug.

Edit: are you making a new session or loading an old one?

---

### Post by djpenguin on 2008-09-25
> **Stochastic said:**
> Segmentation faults are nasty bugs that should be filed on launchpad.  Particularly if it's a fresh install - things should be working perfectly.  The devs should have better answers & they will respond to a launchpad bug.

Edit: are you making a new session or loading an old one?

It doesn't matter if I start a new session or open an existing one, it still segfaults in the same spot.

Pardon my ignorance, but what is launchpad?

---

### Post by Stochastic on 2008-09-25
[https://launchpad.net/](https://launchpad.net/)
It is ubuntu's official bug reporting system.  Developers work with it and get e-mails for any bug filed in their 'watched projects'.  There are many other features of that site, but that's the main one for beginners to be aware of.

---

### Post by djpenguin on 2008-09-25
Okay, I've reported the bug on launchpad, hopefully it gets fixed soon.

---

