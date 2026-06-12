---
title: "Background  Apps on Dash"
date: 2014-01-22
forum: Ubuntu Development Version
---

### Post by Xgen on 2014-01-22
With gnome shell 3.10, background apps such as conky and screenlets now show as icons on the dash. Possible to prevent that?

---

### Post by lonniehenry-gmail on 2014-01-22
Happens to me also.  I had a second partition with gnome-shell version 3.11 and it didn't show up there.  I reinstalled gnome and it had default 3.10 and it appears when I use conky even from startup.  Off to launchpad to search for bugs

---

### Post by cariboo on 2014-01-22
Wouldn't it be just as easy to remove the *.desktop files from /usr/share/applications, then create a bug report, asking that when those packages are created, that they don't create *.desktop files during the install process.

---

