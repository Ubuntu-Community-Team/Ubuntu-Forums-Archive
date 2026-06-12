---
title: "rsnapshot.pid lockfile doesn't get removed after backup"
date: 2006-08-14
forum: Server Platforms
---

### Post by tjansson on 2006-08-14
I have this weird problem that my rsnapshot script doesn't remove the /var/run/rsnapshot.pid lockfile. Which makes rsnapshot stop working. This is how it looks like in the logs:
```

12/Aug/2006:04:30:01] /usr/bin/rsnapshot daily: started
[12/Aug/2006:04:30:01] echo 1290 > /var/run/rsnapshot.pid
[12/Aug/2006:04:30:01] /bin/rm -rf /backup/daily.6/
[12/Aug/2006:04:30:02] mv /backup/daily.5/ /backup/daily.6/
[12/Aug/2006:04:30:02] mv /backup/daily.4/ /backup/daily.5/
[12/Aug/2006:04:30:02] mv /backup/daily.3/ /backup/daily.4/
[12/Aug/2006:04:30:02] mv /backup/daily.2/ /backup/daily.3/
[12/Aug/2006:04:30:02] mv /backup/daily.1/ /backup/daily.2/
[12/Aug/2006:04:30:02] /bin/cp -al /backup/daily.0/ /backup/daily.1/
[12/Aug/2006:04:30:03] /usr/bin/rsync -av --delete --numeric-ids --relative --delete-excluded /home/ /backup/daily.0/localhost/
[12/Aug/2006:04:30:50] /usr/bin/rsync -av --delete --numeric-ids --relative --delete-excluded /etc/ /backup/daily.0/localhost/etc/
[13/Aug/2006:04:30:01] /usr/bin/rsnapshot daily: started
[13/Aug/2006:04:30:01] /usr/bin/rsnapshot daily: ERROR: Lockfile /var/run/rsnapshot.pid exists, can not continue!
[13/Aug/2006:04:30:01] /usr/bin/logger -i -p user.err -t rsnapshot /usr/bin/rsnapshot daily: ERROR: Lockfile /var/run/rsnapshot.pid exists, can not continue
[14/Aug/2006:03:30:01] /usr/bin/rsnapshot weekly: started
[14/Aug/2006:03:30:01] /usr/bin/rsnapshot weekly: ERROR: Lockfile /var/run/rsnapshot.pid exists, can not continue!
[14/Aug/2006:03:30:01] /usr/bin/logger -i -p user.err -t rsnapshot /usr/bin/rsnapshot weekly: ERROR: Lockfile /var/run/rsnapshot.pid exists, can not continue

```

Does anybody have the same problem? For the moment I made a cronjob deleting the pid file every morning at 6, so the script should be running every night now, but it seem so strange?

---

### Post by tjansson on 2006-08-14
Now I tried to do a manual "rsnapshot weekly" and a "rsnapshot daily" which worked fine and when I afterwards look in the /var/run/ folder ther was no rsnapshot.pid file, so I really can't see why doesn't delete the file when running via cron?

---

### Post by exsysprog on 2007-09-17
I am now having the same problem.  Would be great to hear from anyone else who has had this difficulty ...

---

### Post by exsysprog on 2007-09-17
FYI for anyone who may stumble across this while investigating an rsnapshot implementation.  I am running this on feisty desktop and I'm using it to back up two windows machines.  It works like a charm when I run it (sudo) from the command line.  When it runs from cron it stops at various, seemiingly random points.  The verbose logs show abrupt termination, without any error message, sometimes during the roll-up process, sometimes after rsyncing one machine but not starting the next, and sometimes after completing every step exept rm'ing the pid/lock file and "touch"ing the most recent hourly increment..

I'm at a bit of a loss as I see zillions of folks recommending this solution is several forums so ... I know it works.  Maybe I'll crank the logs all the way up to "debug" to see if I can get some useful information.

---

### Post by exsysprog on 2007-09-17
SOLVED - Apparently ...

See the following threads
[http://ubuntuforums.org/showthread.php?t=500687&highlight=rsnapshot+crontab](http://ubuntuforums.org/showthread.php?t=500687&highlight=rsnapshot+crontab)

[http://kubuntuforums.net/forums/index.php?topic=3085000.msg79527#msg79527](http://kubuntuforums.net/forums/index.php?topic=3085000.msg79527#msg79527)

[http://ubuntuforums.org/showthread.php?t=488856&highlight=crontab+mailto](http://ubuntuforums.org/showthread.php?t=488856&highlight=crontab+mailto)

[http://www.hmug.org/man/5/crontab.php](http://www.hmug.org/man/5/crontab.php)

I'm a noob so I was unaware that cron will attempt to email the owner of the crontab in certain circumstances but an environment variable must be set to point to the owner and your email subsystem must be configured - neither of which I have done.

I read those threads and set my MAILTO="" in my crontab via 

sudo crontab -e

and all appears to be well.

Next stop - email subsystem setup!!

---

### Post by Saverio on 2008-05-01
Try following exactly what I wrote here:

[http://saverio.bolognani.googlepages.com/backupinlinux]("http://saverio.bolognani.googlepages.com/backupinlinux")

I'm not saying it's the best or the only solution :-) I'm just saying that it works perfectly on my machine, it should work on yours too!

Are you telling crontab that root is the user running rsnapshot?

Ciao, 
 Saverio

---

