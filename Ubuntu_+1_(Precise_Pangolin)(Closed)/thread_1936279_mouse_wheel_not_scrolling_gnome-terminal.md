---
title: "mouse wheel not scrolling gnome-terminal"
date: 2012-03-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by travishume on 2012-03-05
All and all precise is working w/out problem for me. I'm using gnome 3 desktop with ricotz ppa enabled.

I'm unable to scroll my gnome terminals with my mouse wheel or the touchpad 2-finger scroll. This used to work. 

I wasn't able to find any filed bugs but thought I'd check in here before filing one.

Anyone?


Thanks

---

### Post by jbicha on 2012-03-05
That's a new bug in GTK 3.3.18 which isn't in Precise yet.

---

### Post by travishume on 2012-03-05
Awesome, thanks for the info.

---

### Post by t.rei on 2012-03-06
It seems to me, this is present in all gtk3 apps in precise now? Same configuration of sources as the OP: precise + ricotz testing.

---

### Post by travishume on 2012-03-06
That hasn't been my experience. Only terminal windows are not scrolling. gedit for instance scrolls fine.

---

### Post by hugmenot on 2012-03-06
Thanks for the info, Jeremy.

---

### Post by jbicha on 2012-03-06
This was filed as [bug 948612]("http://pad.lv/948612") now that GTK 3.3.18 has landed in Precise.

---

### Post by mc4man on 2012-03-06
Affects a number of app windows -  scroll down works, scroll up doesn't

---

### Post by dino99 on 2012-03-07
on i386 logged as gnome-classic,  no trouble for scrolling with firefox, but cant with nautilus

---

### Post by mc4man on 2012-03-08
> **dino99 said:**
> on i386 logged as gnome-classic,  no trouble for scrolling with firefox, but cant with nautilus

Dino - this bug (fix released) should resolve all the scrolling issues on 32 bit except for the terminal one
[https://bugs.launchpad.net/ubuntu/+source/libxi/+bug/949465](https://bugs.launchpad.net/ubuntu/+source/libxi/+bug/949465)

---

### Post by jbicha on 2012-03-08
```

This bug was fixed in the package vte3 - 1:0.31.0-0ubuntu2
 ---------------
vte3 (1:0.31.0-0ubuntu2) precise; urgency=low
   * Add debian/patches/03_set_scroll_mask.patch: Explicitly set
    GDK_SCROLL_MASK as recent gtk+ versions require it for scrolling to work.
    (LP: [#948612]("https://bugs.launchpad.net/bugs/948612"))
 -- Martin Pitt      Thu, 08 Mar 2012 10:32:46 +0100

```

---

### Post by travishume on 2012-03-08
Fixed confirmed for terminals.

---

