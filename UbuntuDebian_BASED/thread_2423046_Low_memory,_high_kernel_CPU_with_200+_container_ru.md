---
title: "Low memory, high kernel CPU with 200+ container running"
date: 2019-07-16
forum: Ubuntu/Debian BASED
---

### Post by lcpleung on 2019-07-16
Hi all,

System info:
1) single ubuntu 16.04 LTS, kernel 4.15.0-39-generic
2) k8s 1.11.9, docker 18.06.3
3) 210 containers

  I ran into a problem with kernel memory manager going into high CPU.
  as described here: [https://bugzilla.kernel.org/show_bug.cgi?id=200627](https://bugzilla.kernel.org/show_bug.cgi?id=200627)  
  and fixed here (according to post) -->  [https://lore.kernel.org/lkml/153063052519.1818.9393587113056959488.stgit@localhost.localdomain/T/#m41c9eab50fc96f80572c6e2a605532eb6154d431](https://lore.kernel.org/lkml/153063052519.1818.9393587113056959488.stgit@localhost.localdomain/T/#m41c9eab50fc96f80572c6e2a605532eb6154d431)

 The fix indicated to be in 4.19  and tracing the commits in git, t seems is only in 4.19+ (matching the bug's version)

 Question:  Is there a patch version for 4.15  or 4.18?  (in any of existing ubuntu LTS releases?)

Many thanks!

---

