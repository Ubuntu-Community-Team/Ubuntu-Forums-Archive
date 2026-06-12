---
title: "How to use Ubuntu Kernel Headers"
date: 2012-08-28
forum: Ubuntu Application Development
---

### Post by nehalahoti28 on 2012-08-28
I'm writng a list program using kernel header list.h but facing issues.

Can anyone please provide me a tutorial to start it ?

I'm getting below error:
error: list.h: No such file or directory

---

### Post by Szor3n on 2012-08-28
It sounds like your kernel headers may not be installed. Also keep in mind, you need to include linux/list.h not simply list.h.

---

### Post by nehalahoti28 on 2012-08-30
> **Szor3n said:**
> It sounds like your kernel headers may not be installed. Also keep in mind, you need to include linux/list.h not simply list.h.
Thanx for replying!!
I have modified the file list.h n nw it's working.

---

