---
title: "Difference between memmory usage reports"
date: 2009-10-12
forum: Server Platforms
---

### Post by dragos2 on 2009-10-12
htop shown me a usage of ~ 4 Gb of RAM but free -m shows this

```

dragos@deb02:/$ free -m
             total       used       free     shared    buffers     cached
Mem:         16071      10688       5382          0        228       6800
-/+ buffers/cache:       3659      12411
Swap:        40400          0      40400

```As you can see swap is not activated since it has a lower priority.

Why this difference ?

---

### Post by GuyCorngood on 2009-10-12
Wow, that's a lot of RAM. I'm jealous. :P

Linux uses free RAM to cache various things, mostly disk I/O. The second line of free's output ("-/+ buffers/cache") should match htop's report.

---

