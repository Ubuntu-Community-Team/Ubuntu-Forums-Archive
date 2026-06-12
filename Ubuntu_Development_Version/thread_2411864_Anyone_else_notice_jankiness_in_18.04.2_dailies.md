---
title: "Anyone else notice jankiness in 18.04.2 dailies?"
date: 2019-02-04
forum: Ubuntu Development Version
---

### Post by dankegel on 2019-02-04
I just filed [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1814607](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1814607)
for a half-second recurring display hang on 18.04.2 daily build.
This is on the new Frankencpu from Intel + AMD, it's an i7 with an AMD gpu in the same package.
The same hardware worked fine with kernel 4.15 and 18.04.1, so it seems like a regression...

---

### Post by amano on 2019-02-05
Just with Chromium?
Just on Xorg or on Wayland as well?

---

