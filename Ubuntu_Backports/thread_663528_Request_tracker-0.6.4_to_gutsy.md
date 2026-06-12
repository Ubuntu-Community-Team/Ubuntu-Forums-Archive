---
title: "Request: tracker-0.6.4 to gutsy"
date: 2008-01-10
forum: Ubuntu Backports
---

### Post by simontol on 2008-01-10
I'm here to request Tracker 0.6.4 backporting to Gutsy.
The current 0.6.3 version has a lot of bugs and sometimes raises my cpu usage to 60/70%...
The current tracker-search-tool sucks too.
I've tested 0.6.4 on Hardy and it seems to work fine, but I want to see if the bugs are fixed.
To do this I have to test it in my everyday use.
Thanks,
Simone

---

### Post by flitzjoy on 2008-01-15
+1

Tracker 0.6.4 released

Changelog:
**Fixed memory leaks**
Fixed several crashes
Made indexing more robust by pausing if disk space is low or index grows too big
Limit log file size
New tracker applet - animates when indexing, provides ability to pause indexing as well as viewing status and progress feedback from indexer, statistics, prefs and of course search. Also provides notification of warnings from tracker
New power management options enable much better customization
Ignored files fixes
Deskbar/tracker integration fixes
Made most prefs live and affect tracker in real time. Others will prompt for restart and/or reindex where necessary
Shell script fixes
Fixed Imap bug with embedded Auth in URI
Built in corruption check and scan when tracker not shut down cleanly prevents infinite looping
Fix index deletions
**many more bug fixes and stability improvements**

Please someone pack a backport!

---

### Post by chrisccoulson on 2008-01-15
[https://help.ubuntu.com/community/UbuntuBackports]("https://help.ubuntu.com/community/UbuntuBackports")

---

### Post by chrisccoulson on 2008-01-15
In fact, quick search on Launchpad shows its already requested: [https://bugs.launchpad.net/gutsy-backports/+bug/175676]("https://bugs.launchpad.net/gutsy-backports/+bug/175676")

---

### Post by satkata on 2008-03-02
I posted here an apt-repo, containing those packages.

[http://ubuntuforums.org/showthread.php?t=637834&highlight=tracker+backports](http://ubuntuforums.org/showthread.php?t=637834&highlight=tracker+backports)

---

