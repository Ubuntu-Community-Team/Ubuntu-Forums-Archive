---
title: "Firefox Launches Automatically as root a week after 16.04 update"
date: 2016-09-04
forum: Security
---

### Post by david504 on 2016-09-04
For some reason, my firefox launches as superuser after 16.04 upgrade. How do I fix that?

My update was 12.04 to 16.04
It never did that before. What is odd it was one week later it did this. I'm thinking it was an update after the new version installed.

also my menu bar disappears intermittently, so I enable it again then after a few times of closing the browser it removes the menu bar.

I deleted the desktop icon. it was launching as root without password.

the one in the menu launches normally, but when I drag it to the desktop it launches as superuser without prompting a password.

---

### Post by ajgreeny on 2016-09-04
Use commands ```
sudo updatedb
locate autostart | grep firefox
``` to see if that gives you any clues as to why FF keeps starting.  You may then be able to remove whatever it is (a firefox.desktop file?) that starts it, though why as root is a bit of a mystery.

---

### Post by david504 on 2016-09-07
I don't know what caused it to fix itself but after a few times of turning off and on the computer, the problem mysteriously went away

---

