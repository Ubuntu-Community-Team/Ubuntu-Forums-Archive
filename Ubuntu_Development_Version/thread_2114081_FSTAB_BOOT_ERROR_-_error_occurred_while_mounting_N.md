---
title: "FSTAB BOOT ERROR - error occurred while mounting NOT"
date: 2013-02-09
forum: Ubuntu Development Version
---

### Post by conquerorodueko on 2013-02-09
UBUNTU 13.04 daily build:

Adjustments usually done in previous versions of ubuntu now kick up a fuss.... sadly, regardless of adjustments made, the error does not go away.

I get this annoying error at boot-up
[error occured while mounting NOT]

I HAVE FOUND THE PROBLEM - IT DOES NOT ACCEPT MOUNTING AS [TMPFS]
If you intend to install UBUNTU13.04 daily build do not mount as tmpfs in the fstab.

---

