---
title: "libc6"
date: 2005-05-08
forum: Ubuntu Backports
---

### Post by rwabel on 2005-05-08
Is there any chance to get a backport for the libc6 packages and locales from breezy? Or are there too many dependency problems?

---

### Post by jdong on 2005-05-08
No, it won't be possible. Introducing a new libc would break every package :)

---

### Post by rwabel on 2005-05-09
o I see, that's sad :-)
I've to wait for breezy

---

### Post by TorQ on 2005-05-11
Does this mean that if libc6 gets updated through installing another package it will break my system?

---

### Post by jdong on 2005-05-11
Depends. When Ubuntu releases **official** libc6 updates, they are made sure to be binary-compatible with all current software.


However, if you're getting libc6 updates from anywhere else (i.e. Sid/Sarge repos, 3rd party APT repos), you run a very high chance of breaking your system.

---

