---
title: "tasksel fails when selecting LAMP in beta install (XENIAL)"
date: 2016-03-08
forum: Server Platforms
---

### Post by cincibluer6 on 2016-03-08
No results on a search. Basically I downloaded a March 7 and March 8 build of the Xenial beta and tasksel fails when selecting LAMP. It can install the other packages fine (DNS, OpenSSH, etc.) but fails on LAMP.
Same deal if you bypass it and then invoke tasksel from the fresh build.
Anyone having the same issue? Just wondering if I'm doing something wrong or if I should go ahead and put a bug in the tracker.

---

### Post by m-fahadirshad on 2016-08-05
try use

# sudo tasksel

then install webserver from list. I hope it will work for you .

---

