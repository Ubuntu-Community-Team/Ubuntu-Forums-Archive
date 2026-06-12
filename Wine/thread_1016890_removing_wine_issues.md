---
title: "removing wine issues"
date: 2008-12-20
forum: Wine
---

### Post by Jin127 on 2008-12-20
so I tried to remove wine, and I think everything's alright now, but just wondering what this meant.  I saw this after typing "sudo apt-get remove wine" and uninstalling wine:

The following packages were automatically installed and are no longer required:
  libfreebob0 wine-gecko linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
  libglide2 ttf-liberation libgii1 libgii1-target-x winbind
Use 'apt-get autoremove' to remove them.

Well because I'm just stupid, I autoremoved.  Then my firefox kinda went blank and I couldn't see stuff in firefox anymore.  I went back and used terminal to install the stuff again, so I hope everything's fine now >.>.  What happened?

---

### Post by hikaricore on 2008-12-20
I believe this was just a conincidence.

Some of those packages may have been left over from something else you removed or a distribution upgrade.
As long as everything is fine after a reboot I wouldn't even worry about it.

---

