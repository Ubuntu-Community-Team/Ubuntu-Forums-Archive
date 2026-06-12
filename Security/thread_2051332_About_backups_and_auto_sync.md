---
title: "About backups and auto sync"
date: 2012-09-01
forum: Security
---

### Post by elemenophee on 2012-09-01
I have 2 HDs, one with system (/home included) and the other with another data for example downloads, etc...

I'm looking for a program where I can backup some folders (basically documents, music and pictures) in the second one, automatically.

Any suggestion? If you know anyone for Windows let me know too.

---

### Post by Lars Noodén on 2012-09-01
The best program for that kind of backup would be [rsync](https://help.ubuntu.com/community/rsync).  You could call it via [cron](https://help.ubuntu.com/community/CronHowto) so that it is run at specific times or intervals.  Or you could experiment with inotify which will run programs or scripts when certain files or directories change.

---

### Post by HermanAB on 2012-09-02
Howdy,

Use DejaDup.  It is easy to use and uses rsync underneath.

---

### Post by elemenophee on 2012-09-03
Those are for daily update, but I need real time synchronization.

---

### Post by Lars Noodén on 2012-09-03
> **elemenophee said:**
> Those are for daily update, but I need real time synchronization.

Then look into calling rsync from inotify, in particuar [incron](http://linux.die.net/man/1/incrontab).

---

### Post by elemenophee on 2012-09-03
I got one working very well already, FreeFileSync. And it works perfect in both Linux and Windows.

---

