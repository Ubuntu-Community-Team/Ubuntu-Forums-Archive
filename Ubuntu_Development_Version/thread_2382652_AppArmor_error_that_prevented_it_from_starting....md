---
title: "AppArmor error that prevented it from starting..."
date: 2018-01-16
forum: Ubuntu Development Version
---

### Post by zika on 2018-01-16
Correct  line #11 in /etc/apparmor.d/snap.core.3604.usr.lib.snapd.snap-confine by adding space after #... That puts AppArmor again in business for those using it...

---

