---
title: "nm-applet leaking ram lately"
date: 2012-02-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Quackers on 2012-02-15
It seems that nm-applet is leaking ram again. Didn't this happen about this stage in OO?
System uptime of 13 hours and it's using 309MB ram at the moment. Actually it's 310MB now :D
It'll be up to 500MB soon enough.

---

### Post by dino99 on 2012-02-15
i cant count nm issues as they are numerous since a while, so im happy now with wicd
but i've already seen lately the same issue than yours

---

### Post by Quackers on 2012-02-15
313MB now and climbing

---

### Post by dino99 on 2012-02-15
> **Quackers said:**
> 313MB now and climbing

:) next time you'll get the jackpot :)

maybe its time to run valgrind with this borked id

---

### Post by Quackers on 2012-02-15
> **dino99 said:**
> :) next time you'll get the jackpot :)
:-) :-) :-)

---

### Post by mc4man on 2012-02-15
bug - 
[https://bugs.launchpad.net/bugs/930491](https://bugs.launchpad.net/bugs/930491)

The more available networks the larger the leak - here with 16 or so it was about 1MiB per min. (got tired of it so removed & switched to Wicd

---

### Post by Quackers on 2012-02-15
> **mc4man said:**
> bug - 
[https://bugs.launchpad.net/bugs/930491](https://bugs.launchpad.net/bugs/930491)

The more available networks the larger the leak - here with 16 or so it was about 1MiB per min. (got tired of it so removed & switched to Wicd
Thanks mc4man, I've me too'd

---

### Post by Finalfantasykid on 2012-02-15
I remember experiencing this bug.  If I remember correctly, it had to do with the memory of the image used in the applet not being freed whenever the status changes.  At home this might not be so bad as the connection should be reasonable constant, but somewhere else, where it is constantly fluctuating, could be a bad thing.

This is was I remember reading back then, and it might not have actually been true, or it might not be the case this time around.

---

