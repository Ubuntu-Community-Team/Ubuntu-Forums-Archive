---
title: "[Backport] tracker 0.6.4"
date: 2007-12-11
forum: Repositories &amp; Backports
---

### Post by spanella47 on 2007-12-11
new version of tracker was just released and fixes many bugs exhibited in Gutsy's version (0.6.3) - such as high memory usage, exclusion directories not being deleted from index, and many more annoyances.  Mostly a bug fix release besides the new applet.

[http://mail.gnome.org/archives/tracker-list/2007-December/msg00031.html](http://mail.gnome.org/archives/tracker-list/2007-December/msg00031.html)

---

### Post by watchmancole on 2007-12-19
+1 on this. Backporting the new version of tracker is needed if not for the other improvement do it just to have a more stable desktop.

---

### Post by Sector on 2007-12-19
I also agree on this 100%, tracker 0.6.3 is just causing too much "problems" across the board. If this changelog is to be believed, 0.6.4 will provide a lot of relief for the people using backports. I would not hesitate a second to update it.

---

### Post by Peterix on 2007-12-19
+1
This is absolutely needed because 0.6.3 segfaults when indexing e-mail from evolution with more than 256 recipients. I can't make it work without deleting my mail.

---

### Post by Götz on 2007-12-27
+1
I think also it sould be backported, because tracker has few problems for many people.

---

### Post by acheton on 2008-01-23
I have some problems with tracker too, I've looked on getdeb and can't see a backport. Does anyone know if a package for Gutsy is available yet?

---

### Post by satkata on 2008-03-02
Here is a apt repo, which provides a backported tracker 0.6.4 packages:

deb [http://ppa.launchpad.net/pochu/ubuntu](http://ppa.launchpad.net/pochu/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/pochu/ubuntu](http://ppa.launchpad.net/pochu/ubuntu) gutsy main


But I would rather ask, if someone knows of backported packages from the latest version, which is now 0.6.5

Thanks

P.S. I just checked out the repo and saw, that the maintainer has already built tracker-0.6.5-packages, but these are not compatible with gutsy. :(

---

