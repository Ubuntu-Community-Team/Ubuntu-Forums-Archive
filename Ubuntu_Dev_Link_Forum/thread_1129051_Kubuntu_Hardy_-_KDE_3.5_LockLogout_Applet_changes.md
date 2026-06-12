---
title: "Kubuntu Hardy - KDE 3.5 Lock/Logout Applet changes"
date: 2009-04-18
forum: Ubuntu Dev Link Forum
---

### Post by and.hunt on 2009-04-18
Yesterday I did a large system update on my system running Ubuntu Hardy with KDE 3.5,and an unwanted change came about:
 I have my main kicker bar set at height of 40 pixels, and also use the Lock/Logout button applet. Before the update the two buttons in the applet (lock & logout) were one above the other (the way I prefer), after the change the two buttons are side by side. In the new version of the applet the kicker bar needs a height of 44 pixels for the buttons to be one above the other. (The way I want is in packageL kicker (4:3.5.9-0ubuntu7), the update is: kicker (4:3.5.10-0ubuntu1~hardy2) ). I managed to return to the initial setup by unpacking the original package and extracting the required file from it (/usr/lib/kde3/lockout_panelapplet.so). This change happened because of the following kde svn update:
[http://websvn.kde.org/?view=rev&revision=848270](http://websvn.kde.org/?view=rev&revision=848270)
I think it might possibly be an idea to revert to the original panel applet for those with my setup (however I don't know whether anyone else actually has this setup). Alternatively a better idea might be to allow scaling of the applet, with user configuration, so that they can choose themselves what orientation of buttons they want.

---

