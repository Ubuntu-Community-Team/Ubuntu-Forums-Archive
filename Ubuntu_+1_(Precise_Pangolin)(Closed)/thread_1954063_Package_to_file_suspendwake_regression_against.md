---
title: "Package to file suspend/wake regression against?"
date: 2012-04-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by tehowe on 2012-04-07
My notebook's ([_Acer 1410_]("http://ncix.com/products/?sku=45412")) suspend/wake cycle was broken in Beta 1, then that was fixed after a while, and now within the last week it's been waking to an unresponsive terminal screen with a cursor flashing in the top left.

What package would I file this bug against - or if it's the kernel, what do I do in that case? Also since that's thin gruel for a developer, how could I include any useful information?

---

### Post by 2F4U on 2012-04-07
I would say that pm-utils would be the right package to report against. With respect to information to include, I would start by including the system log file, dmesg, pm-suspend.log and as much detail about your hardware configuration as possible.

---

