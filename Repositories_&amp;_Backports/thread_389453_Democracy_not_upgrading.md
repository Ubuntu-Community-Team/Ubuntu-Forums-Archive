---
title: "Democracy not upgrading"
date: 2007-03-20
forum: Repositories &amp; Backports
---

### Post by cactaur on 2007-03-20
I'm wondering if anyone else has this problem, but the update manager is on for me, and telling me to update Democracy player to 9.5.3. I installed it the [repository way]("http://www.getdemocracy.com/downloads/ubuntu.php"). However, when I try to update I get this error:

```
W: Failed to fetch http://ftp.osuosl.org/pub/pculture.org/democracy/linux/repositories/ubuntu/edgy/democracyplayer-data_0.9.5.3-1ubuntupcf_all.deb
  404 Not Found


W: Failed to fetch http://ftp.osuosl.org/pub/pculture.org/democracy/linux/repositories/ubuntu/edgy/democracyplayer_0.9.5.3-1ubuntupcf_i386.deb
  404 Not Found
```

I know this isn't Ubuntu's fault, but does anyone else get this problem?

---

### Post by warkro on 2007-03-22
i can't upgrade either...I don't get that error.  my repo still says 0.9.5.1.  I think the FTP still hasn't been updated.  I would wait a day.

---

### Post by thedude98 on 2007-03-26
I am having the same issue.  Will this resolve itself?  Any guidance greatly appreciated.

---

### Post by helpdeskdan on 2007-03-29
It is literally NOT there.  You can look for yourself:
[http://ftp.osuosl.org/pub/pculture.org/democracy/linux/repositories/ubuntu/edgy/](http://ftp.osuosl.org/pub/pculture.org/democracy/linux/repositories/ubuntu/edgy/)

Why it thinks it IS there, I have no idea, it's not listed in the packages.  I also have no idea whom to bug about it.  pculture.org maybe.  For now, just put a # in front of it in your /etc/apt/sources.list.  If you are really motivated, you can go built it from source.  
[http://www.getdemocracy.com/downloads/#linux](http://www.getdemocracy.com/downloads/#linux)

More info:
[http://www.getdemocracy.com/news/2007/03/minor-update-democracy-player-0953/](http://www.getdemocracy.com/news/2007/03/minor-update-democracy-player-0953/)

---

### Post by thedude98 on 2007-04-01
Synaptic was finally able to update these 2 packages yesterday.  So it seems it was a self fix.  Those are the best kind. ;)

---

