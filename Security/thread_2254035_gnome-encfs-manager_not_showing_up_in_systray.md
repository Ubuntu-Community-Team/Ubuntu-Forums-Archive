---
title: "gnome-encfs-manager not showing up in systray"
date: 2014-11-24
forum: Security
---

### Post by john294 on 2014-11-24
Hi,
I'm using ubuntu 14.04 with an xfce4-desktop
I recently installed the gnome-encfs-manager which I've happily been using on my other Xubuntu system for a time now (as cryptkeeper from the standard-repositories never worked at all for me).
On my Ubuntu (xfce) system, the gnome-encfs-manager is running, but does not show up in the systray. No GUI can be invoked.
A quick google-search did not provide a clear solution to this problem. Apparently other people found an enc-fs-symbol in their hidden "task-bar" at the bottom of the screen. I, however, do not have such a taskbar and do not know how to invoke it.
Any suggestions?

---

### Post by Toz on 2014-11-25
Make sure you have the Indicator Plugin added to your panel - it will show up there. Note that the Indicator Plugin is different than the Notification Area (systray).

---

### Post by john294 on 2014-11-28
Yes, That was the problem. Works now. Thanks a lot!

---

