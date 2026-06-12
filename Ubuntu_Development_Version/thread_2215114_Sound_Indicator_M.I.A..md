---
title: "Sound Indicator M.I.A."
date: 2014-04-04
forum: Ubuntu Development Version
---

### Post by bug67 on 2014-04-04
After yesterday's updates that [broke sound]("http://ubuntuforums.org/showthread.php?t=2211608") among other things,  sound was fixed with yet another update.  However, the sound indicator in the panel has gone missing and I can't seem to get it back.  Any ideas?

---

### Post by Toz on 2014-04-04
The [xubuntu-devel mailing list]("https://lists.ubuntu.com/archives/xubuntu-devel/2014-April/thread.html") has a thread regarding xfce4-indicator-plugin issues, of which one is the missing sound indicator. Its being worked on. Here is the launchpad bug: [https://bugs.launchpad.net/ubuntu/+source/xfce4-indicator-plugin/+bug/1302571]("https://bugs.launchpad.net/ubuntu/+source/xfce4-indicator-plugin/+bug/1302571").

---

### Post by bug67 on 2014-04-04
Thanks for the info.  :)

---

### Post by spsf2 on 2014-04-10
Just tested the daily ISO today 2014/apr/10 (RC date)
Still not appearing on the first boot with live USB, did not try to install yet
If you enable it in auto start and log out/in it works but with duplicated bluetooth indicators, weird...

---

### Post by QDR06VV9 on 2014-04-10
> **spsf2 said:**
> Just tested the daily ISO today 2014/apr/10 (RC date)
Still not appearing on the first boot with live USB, did not try to install yet
If you enable it in auto start and log out/in it works but with duplicated bluetooth indicators, weird...
I also can confirm.
But after hand compiling pulseaudio from git seems to fix it.
To Compile pulse from [git]("http://ubuntuforums.org/showthread.php?t=2210602")
Regards

---

### Post by frank18 on 2014-04-10
hi guys I've been having the same problem since Xubuntu 12.04 and now Xubuntu 1404 beta
I do a clean install with added updates at install, sound indicator is good now if i go to software update and install more updates then i loose the sound indicator,now i'm not gonna update no more till sound bug is fixed,or at least someone please tell me the code to solve the issue,thanks

---

