---
title: "Top Panel Transparency Issues"
date: 2012-10-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by victor9098 on 2012-10-04
Hi All,

Setting the top panel transparency to 0 leads to the window names and options overlapping themselves until you click around in the screen for a bit. But selecting a window causes it to happen again. See the attached image for a better idea.

This has been a problem in the last few cycles for me but was wondering if anyone else suffers the same or what I should file a bug against?


Thanks!

---

### Post by mc4man on 2012-10-04
longstanding issue starting in 12.04
It was 'inadvertently' fixed early in 12.10 around unity 6.0/whatever compiz, then came back around 6.2/whatever compiz
[https://bugs.launchpad.net/unity/+bug/924592](https://bugs.launchpad.net/unity/+bug/924592)

It's now being tracked in a new bug here &  attributed to the GLES compiz merge though no fix as of yet
[https://bugs.launchpad.net/unity/+bug/1044021](https://bugs.launchpad.net/unity/+bug/1044021)

At one point in 12.04 a workaround was to use an opacity of 0.0100 which would appear fully trans but would hide the underlying text. However the scale of opacity then broke & no longer reduces linearly so in general the option itself remains  messed up & the workaround is of no use
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/963505](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/963505)

---

### Post by victor9098 on 2012-10-04
I could have sworn the last time I tried it out nothing was wrong, only was messing now and saw it had come back. Yes, I tried setting to .0100 but the font looks all messed up in the Radiance theme at least, not as bad in Ambiance.

Will add myself to the bugs.

Thanks again mc4man

---

