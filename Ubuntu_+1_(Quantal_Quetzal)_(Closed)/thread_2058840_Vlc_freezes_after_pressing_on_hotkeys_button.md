---
title: "Vlc freezes after pressing on hotkeys button"
date: 2012-09-16
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by GreatDanton on 2012-09-16
Yesterday I tried to change hotkeys in vlc, however after I pressed hotkeys button (under preferences) vlc freezes, and so does my desktop. After a while I got black screen. If I press ctrl+alt+delete I am able to log out, and log in again.

Anyone came around this problem?
If so here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/1051701](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/1051701)

Regards.

---

### Post by balloons on 2012-09-18
You've found the liboverlay bug!

[https://bugs.launchpad.net/ayatana-scrollbar/+bug/1005677](https://bugs.launchpad.net/ayatana-scrollbar/+bug/1005677)

I confirmed your bug and that it was liboverlay this morning.

---

### Post by GreatDanton on 2012-09-18
Thank you guitara. If anybody has the same problem type this in terminal:
> LIBOVERLAY_SCROLLBAR=0 vlc

After that you should be able to press on hotkeys tab.

Regards.

---

