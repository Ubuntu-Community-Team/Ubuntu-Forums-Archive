---
title: "Needing WINE output (Kindle)"
date: 2011-01-31
forum: Wine
---

### Post by Ckesey on 2011-01-31
I'm trying to run the (PC) Kindle application on Ubuntu 10.10.

I have followed several of the online tutorials on how to install and run. Seems about the same as any other WINE application.

When I try to start the .exe I get only get this for output:

fixme:system:SetProcessDPIAware stub!

From what little I understand this isn't really an error.  After this I get dumped back to the CLI.

Is there any other place I can look to see why the application isn't trying to start???

---

### Post by cogadh on 2011-01-31
What version of Wine and the Kindle app are you trying to run? Looking at the [AppDB page for it]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=10597"), it looks like the app will not work on Wine 1.2.X, but will on the unstable 1.3.X version. Additionally, the newest version of the Kindle app seems to work the best.

---

