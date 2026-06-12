---
title: "Upgrading to Breezy"
date: 2005-08-31
forum: Ubuntu Backports
---

### Post by NeoChaosX on 2005-08-31
I'm thinking of upgrading from Hoary to Breezy next week when the preview release of Breezy hits. Since I'm a big fan of the backports, will I need to roll back any installed backported packages to their original Hoary versions like one had to do when going from Warty to Hoary with Warty backports installed? Or will the packages upgrade without any problems? Just really want to know.

---

### Post by duffman25 on 2005-09-01
[QUOTE=NeoChaosX]I'm thinking of upgrading from Hoary to Breezy next week when the preview release of Breezy hits. Since I'm a big fan of the backports, will I need to roll back any installed backported packages to their original Hoary versions like one had to do when going from Warty to Hoary with Warty backports installed? [/QUOTE]

I think your answer here is no. 

> Or will the packages upgrade without any problems? Just really want to know.

I've dist-upgrade one of my machines yesterday to breezy & everything went ok (not as smooth as I thought, but it's ok since I could work out the small gliches). One thing that happened, is that I did upgrade with aptitude and some old packages wheren't removed. (ooo1 and the kernel 2.6.10) I had to search for them & purged them after the upgrade.

---

