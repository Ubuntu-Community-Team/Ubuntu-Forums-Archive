---
title: "New gnome-shell (3.3.3) in Ricotz Testing PPA broken"
date: 2012-01-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2012-01-17
The new gnome-shell (3.3.3), mutter (3.3.3), clutter (1.9.3) and cogl (1.9.4), all built against new libcogl7 (instead of libcogl6), are broken.
The whole desktop will hang with these updates.

I suspect this is due to the new clutter-cogl group.

So, do wait until you upgrade.

---

### Post by dino99 on 2012-01-17
as said on top: "use at your own risk" :)

---

### Post by Harry33 on 2012-01-17
I am using at my own risk.
However downgrading to the previous (libcogl6) versions fixed this for now.
Also, new clutter 1.9.4 is already building there.

---

### Post by dino99 on 2012-01-17
> **Harry33 said:**
> I am using at my own risk.
However downgrading to the previous (libcogl6) versions fixed this for now.
Also, new clutter 1.9.4 is already building there.

Thanks Harry, continue to bring fresh news :)

---

### Post by zika on 2012-01-17
```
The following NEW packages will be installed:
  librhythmbox-core4{a} 
The following packages will be REMOVED:
  librhythmbox-core5{u}
```
Step backwards?

---

### Post by Harry33 on 2012-01-17
> **zika said:**
> ```
The following NEW packages will be installed:
  librhythmbox-core4{a} 
The following packages will be REMOVED:
  librhythmbox-core5{u}
```Step backwards?

So it seems, that's odd.

---

### Post by mc4man on 2012-01-17
I believe atm the new ubuntu repo RB will trump the ppa version

---

### Post by Harry33 on 2012-01-17
The newest gnome-shell (3.3.3+git20120217), mutter (3.3.3+git20120117), clutter (1.9.4+git20120116) and cogl  (1.9.4-0ubuntu1), all built against new libcogl7 (instead of libcogl6), fixed the issue.
All is well now.

---

### Post by zika on 2012-01-18
> **Harry33 said:**
> So it seems, that's odd.Yes, I've slipped on that [img]http://www.eatmedaily.com/wordpress/wp-content/uploads/2009/04/adriana-lara-banana-peel.jpg[/img]but did not [img]http://static5.depositphotos.com/1008154/534/i/450/dep_5345688-Slip-and-fall.jpg[/img]dpkg rules... ;)

---

