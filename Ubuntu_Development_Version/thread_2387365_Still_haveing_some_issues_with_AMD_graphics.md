---
title: "Still haveing some issues with AMD graphics"
date: 2018-03-18
forum: Ubuntu Development Version
---

### Post by exploder on 2018-03-18
I am running Ubuntu 18.04 on an old HP dc7800 with an add in AMD R200 graphics card. Most of the time there is no problem and graphics seem just fine. Every once in a while on boot though GDM will come up as a purple screen with some orange streaks. I can still hit enter, type my password, log in and the desktop loads fine after that. Like I said, most of the time GDM looks and works like expected, just every once in a while it does this. Anyone else having this same thing happen?

---

### Post by T.J. on 2018-03-18
It could be just a bug or it could be a hardware problem. I'm sorry I can't test for you. I haven't any example hardware that old.  What it sounds like is a bug in the driver or in GDM (which has been known to have unfixed bugs).  Have you tried replacing it with lightdm?  I would highly recommend it, as lightdm is better tested, IMHO.  If you need help, please post back.

---

### Post by exploder on 2018-03-18
Thanks! I am wondering if GDM is the culprit because everything before and after it is working perfectly.

---

### Post by T.J. on 2018-03-20
I think it is likely that something in GDM is shifting the color palette off.  In saying that, I **cannot **be certain.  It could be a hardware issue.  As long as the card seems to work properly and displays no other aberrant behavior, I think is it simply a bug in GDM or the driver.  I recommend that you report it so that it can be corrected.

---

