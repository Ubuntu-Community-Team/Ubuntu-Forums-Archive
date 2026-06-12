---
title: "Lucid drive check on startup"
date: 2010-05-14
forum: United Kingdom Team
---

### Post by ex-wirecutter on 2010-05-14
I'm glad the occasional automatic drive check is still available on Lucid , 
but unless I am mistaken it seems to take much,much, longer, ages in fact , has anyone else experienced this ?

---

### Post by coffee412 on 2010-05-14
Had the same problem. I dual boot fedora 11 and Ubuntu with a 250 gig sata drive. The filesystem check took forever. Seems to slow down more as it progresses. When the percentage reached around 90 percent it started to progress very slow. I almost thought it had stalled out for some reason.

Shouldnt take that long. Running fsck in a term window is much faster. 

coffee

---

### Post by Ron S on 2010-05-14
Had the same problem. There seems to be a bug in mountall see [https://bugs.launchpad.net/bugs/571707](https://bugs.launchpad.net/bugs/571707) . Installing new package from lucid proposed fixed the problem for me. Disk check time dropped from 30 minutes to 20 secs.
Hope this helps

---

### Post by bgreenaway on 2010-05-17
> **Ron S said:**
> Had the same problem. There seems to be a bug in mountall see [https://bugs.launchpad.net/bugs/571707](https://bugs.launchpad.net/bugs/571707) . Installing new package from lucid proposed fixed the problem for me. Disk check time dropped from 30 minutes to 20 secs.
Hope this helps

Tried this and it seemed to work ok up to 70% then became v-e-r-y slow. From the same thread, I found this, which echoed my symptoms exactly:

[I]OBSERVATIONS

The fsck message "(...) non-contiguous (...)" Which I assume indicates the end of the fsck, is printed in the Virtual Terminal ("outside" plymouth) at around 70% + ~10-20 seconds.

Disk activity is null from this point on (presumed end of fsck above).

Bootchart crashes if trying to catch the whole boot at once with plymouth (at least for my 1h boot).

This problem seems to occur in both plymouthd and mountall, semi-simultaneously:
If you are in the plymouth screen, plymouthd is the cpu-gobbler, if you switch away from it using the arrow keys, mountall instead takes over the cpu-eating.

[/I]

---

