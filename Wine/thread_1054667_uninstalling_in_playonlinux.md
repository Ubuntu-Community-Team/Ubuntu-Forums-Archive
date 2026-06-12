---
title: "uninstalling in playonlinux"
date: 2009-01-29
forum: Wine
---

### Post by Jin127 on 2009-01-29
I tried to use playonlinux to install Last Chaos, but when it was done installing, it never poped up on the list.  It is installed, and I can run it, but now my problem is I want to uninstall it.  it's installed under playonlinux/wineprefix/LastChaos/drive_c/AeriaGames/LastChaosUSA.  I can't figure out a way to get rid of it, since there's no "uninstall.exe", and it's not under wine so running uninstaller under terminal doesn't work.  It's not under the list for Playonlinux either, so that doesnt work.  How can I get rid of it?
Thanks for the help.

---

### Post by cogadh on 2009-01-30
Try running this:
```
env WINEPREFIX=~/playonlinux/wineprefix/LastChaos uninstaller
```
You may need to adjust that WINEPREFIX path a bit, if the path you posted was not 100% accurate; I believe the "playonlinux" directory is actually ".playonlinux", but I'm not certain (I don't use PlayOnLinux anymore).

---

