---
title: "Autorun cd installer with wine"
date: 2009-04-04
forum: Wine
---

### Post by demaxmeister on 2009-04-04
Hi,

I'm trying to install the Sims 2 (check if it works) under Wine, the installer runs fine, but when asked to insert disk 2, I can't run it.
The autorun.inf says:
[autorun]

open=RunGame.exe

Icon=Sims2.ico

Name=The Sims 2



[Special]

Disk=2

I think it needs that special disk=2, but wine doesn't use the autorun.inf.
Can somebody make this work?

thanks

---

### Post by hikaricore on 2009-04-04
The Sims 2 has a garbage rating under WINE.  It will likely not run even if you can install it.
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1942](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1942)

---

