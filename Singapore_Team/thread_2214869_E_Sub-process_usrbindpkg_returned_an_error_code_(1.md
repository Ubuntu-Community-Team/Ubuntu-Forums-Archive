---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2014-04-03
forum: Singapore Team
---

### Post by desmondkung on 2014-04-03
Need help to figure out why can't I uninstall spotify

---

### Post by ian-weisser on 2014-04-03
> Removing spotify-client ...
/var/lib/dpkg/info/spotify-client.prerm: 9: [COLOR=#ff0000]cd: can't cd to /opt/spotify/spotify-client[/COLOR]
dpkg: error processing spotify-client (--purge):

Looks like you (or somebody other than the package manager) manually moved or deleted the application files in /opt/spotify/
The package manager is complaining that it cannot remove those files because they don't exist where it expects to find them.

If you use a package manager, NEVER manually move or delete a package-manager-installed file.
You're not required to use a package manager. You can work manually if you wish.

You have three options:
1) You can reinstall spotify so it can be cleanly uninstalled.
2) You can install a set of dummy files for the package manager to remove.
3) You can force the package manager to consider the package uninstalled, and to ignore whatever litter you didn't remove manually.

Which one do you want to do?

---

### Post by desmondkung on 2014-04-04
Weird thing is I never uninstalled it before. Was trying to bring it up but couldn't find it in my applications installed. Same thing happened to teamviewer, but I managed to solve it by re-installing. Not so for spotify. Just popped me those errors when I tried to re-install. Tried purging it to see if it worked but it didn't.

Trying the solution found here: [http://ubuntuforums.org/showthread.php?t=2190467&page=2](http://ubuntuforums.org/showthread.php?t=2190467&page=2)

---

### Post by ian-weisser on 2014-04-04
[http://ubuntuforums.org/showthread.php?t=2190467&p=12867530#post12867530](http://ubuntuforums.org/showthread.php?t=2190467&p=12867530#post12867530)
Post #20 has an appropriate and safe solution.

---

