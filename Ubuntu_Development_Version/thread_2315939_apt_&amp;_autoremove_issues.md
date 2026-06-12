---
title: "apt &amp; autoremove issues"
date: 2016-03-03
forum: Ubuntu Development Version
---

### Post by mc4man on 2016-03-03
Currently see 1, but that doesn't mean there aren't others.
The one is currently any packages installed via apt-get build-dep will immediately be marked for autoremove. Somewhat counter productive...
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1552962](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1552962)

Fixed with apt 1.26

---

