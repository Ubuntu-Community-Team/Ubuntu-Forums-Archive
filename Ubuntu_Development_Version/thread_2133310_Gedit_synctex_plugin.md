---
title: "Gedit synctex plugin"
date: 2013-04-07
forum: Ubuntu Development Version
---

### Post by AntoineT on 2013-04-07
I recently notices that, although gedit-plugins 3.6.1-0ubuntu1 is installed on my system (raring i386), the SyncTex plugin is missing from the plugins list in Preferences->Plugins (gedit 3.6.2-0ubuntu1).
Could you guys be kind enough to check that you have the same problem on your system, and maybe confirm the bug I opened in Launchpad [https://bugs.launchpad.net/ubuntu/+source/gedit-plugins/+bug/1165742](https://bugs.launchpad.net/ubuntu/+source/gedit-plugins/+bug/1165742)

---

### Post by mc4man on 2013-04-07
Mentioned something in your bug, can build & enable here but not really in a position to test how it works.
If you wish to test let me know, should only take a few min. or so.

---

### Post by AntoineT on 2013-04-08
Thanks Doug, I'll try to build as well.

---

### Post by AntoineT on 2013-04-09
Ok, I managed to build locally (after installing a few packages such as libdbus-1-dev and gedit-dev) and synctex is runnink OK.
I noticed that the Terminal plugin is now unavailable with my local build (as with yours, telling from your screenshot). I don't use it so that's OK.

---

### Post by mc4man on 2013-04-09
> **AntoineT said:**
> Ok, I managed to build locally (after installing a few packages such as libdbus-1-dev and gedit-dev) and synctex is runnink OK.
I noticed that the Terminal plugin is now unavailable with my local build (as with yours, telling from your screenshot). I don't use it so that's OK.
No, it's there, called embedded terminal so higher in the list
Anyone that wanted to use would need may need to disable "use theme colors" in gsetttings or the terminal could be white on white

---

### Post by AntoineT on 2013-04-09
Right. I had to rebuild after installing libvte-2.90-dev and now all plugins appear in the list.
Thanks a bunch

---

