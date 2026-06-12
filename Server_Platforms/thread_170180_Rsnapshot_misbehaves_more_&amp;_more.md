---
title: "Rsnapshot misbehaves more &amp; more"
date: 2006-05-04
forum: Server Platforms
---

### Post by el3ktro on 2006-05-04
Damn this is so freaking strange. Rsnapshot misbehaves more & more. It started a few weeks ago that suddenly rsnapshot wouldn't "touch" the created backup dirs anymore. When rsnapshot is doing a backup at 10:00, it touches the backup dir afterwards, so that the backup dir has a timestamp of 10:00 - so you could easily see when the backup was created. Rsnapshot does this fine, but NOT when run from a cronjob!!

Now it gets even stranger. I deleted all "daily" backup dirs. On the first day, it created daily.0 from the latest hourly backup - just as it should. On the second day, it moved daily.0 to daily.1 and created daily.0 again from the latest hourly.0 But then it stops! The log files says that every day in the evening rsnapshot daily was run, but it doesn't create any new daily directories! I still have a directory daily.1 from a week ago, and I have daily.0 from yesterday evening - and a whole week is missing in between!

This is so strange, it seems to all have to do with my cronjob. When I run the EXACT SAME command as in the cronjob manually (as root) then everything works fine! Even touching the directories work!

Any ideas? I can post the backup script & my crontab if you want em.


Tom

---

