---
title: "No Dash Icon After Packages Install Until New Session"
date: 2015-09-23
forum: Ubuntu Development Version
---

### Post by buzzingrobot on 2015-09-23
Dash isn't finding or displaying an icon for newly installed packages until I start a new session (log out/log in). Desktop files are deposited in /usr/share/applications. I've seen this on multiple installs of 15.10 dailies.

Couldn't find an obvious bug report at Launchpad. Anyone else seeing this?

---

### Post by buzzingrobot on 2015-09-24
In case anyone else sees it, I filed a bug: [https://bugs.launchpad.net/ubuntu/+source/dash/+bug/1499322](https://bugs.launchpad.net/ubuntu/+source/dash/+bug/1499322).

---

### Post by grahammechanical on 2015-09-24
What I have noticed recently is that an update to Firefox & Libreoffice will remove them from the Launcher and they have to be launched & locked. And they will not appear in the Dash recent apps list until re-launched. I have seen the same thing happen to Ubuntu Web Browser which I do not lock to the launcher as I tend to launch it from Dash>recent apps. Ubuntu Software Centre has also been removed from the launcher.

I think that the home lens/scope no longer presents recent used apps. If it ever did. Could be my imagination. Recent used apps appears with the Apps lens/scope.

---

### Post by buzzingrobot on 2015-09-24
Recents Apps in Apps, but not in the Home lens here, as well.

When I install an app, the new desktop file in /usr/share/applications launches it if clicked on, so presumably the package installed correctly.  But, a search returns nothing, and the icon can't be found. Log out and log in, and all's well.

---

