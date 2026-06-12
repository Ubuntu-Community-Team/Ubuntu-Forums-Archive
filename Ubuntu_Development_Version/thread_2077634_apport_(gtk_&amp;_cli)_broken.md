---
title: "apport (gtk &amp; cli) broken"
date: 2012-10-29
forum: Ubuntu Development Version
---

### Post by mc4man on 2012-10-29
bug here
[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1072489](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1072489)
(for the purpose of filing 1 new non crash bug removed 1 arg from line 22 which allowed it to run but obviously not a good idea at all, not advised..

---

### Post by ventrical on 2012-10-29
+1

When I clicked <continue> it just disappeared.

---

### Post by mc4man on 2012-11-06
Fixed in latest apport*, python3-apport (2.6.2-0ubuntu1) to be exact
(it removed 1 arg - verbose, which was what I was doing, guess it wasn't a 'bad idea' afterall.

---

