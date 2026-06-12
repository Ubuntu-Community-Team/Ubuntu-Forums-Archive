---
title: "Tons of Deleted Files That Are Open - Is This a Problem?"
date: 2015-11-02
forum: Server Platforms
---

### Post by Dan_Allen on 2015-11-02
Results of running  lsof|grep delete..  Is this normal?

```
init          1               root   10w      REG              253,1         0    1179863 /var/log/upstart/systemd-logind.log.1 (deleted)
sw-engine  1374               root    3u      REG              253,1         0     262252 /tmp/.ZendSem.0m5vJK (deleted)
mysqld    11819              mysql    4u      REG              253,1         0     262237 /tmp/ibKN3LL5 (deleted)
mysqld    11819              mysql    5u      REG              253,1         0     262239 /tmp/ibLy82XL (deleted)
mysqld    11819              mysql    6u      REG              253,1         0     262240 /tmp/ibgXNkas (deleted)
mysqld    11819              mysql    7u      REG              253,1         0     262242 /tmp/ibrNo5EO (deleted)
mysqld    11819              mysql   11u      REG              253,1         0     262249 /tmp/ib9Rfc0u (deleted)
mysqld    11819 11831        mysql    4u      REG              253,1         0     262237 /tmp/ibKN3LL5 (deleted)
mysqld    11819 11831        mysql    5u      REG              253,1         0     262239 /tmp/ibLy82XL (deleted)
mysqld    11819 11831        mysql    6u      REG              253,1         0     262240 /tmp/ibgXNkas (deleted)
mysqld    11819 11831        mysql    7u      REG              253,1         0     262242 /tmp/ibrNo5EO (deleted)
mysqld    11819 11831        mysql   11u      REG              253,1         0     262249 /tmp/ib9Rfc0u (deleted)
mysqld    11819 11832        mysql    4u      REG              253,1         0     262237 /tmp/ibKN3LL5 (deleted)
mysqld    11819 11832        mysql    5u      REG              253,1         0     262239 /tmp/ibLy82XL (deleted)
mysqld    11819 11832        mysql    6u      REG              253,1         0     262240 /tmp/ibgXNkas (deleted)
mysqld    11819 11832        mysql    7u      REG              253,1         0     262242 /tmp/ibrNo5EO (deleted)
mysqld    11819 11832        mysql   11u      REG              253,1         0     262249 /tmp/ib9Rfc0u (deleted)
mysqld    11819 11833        mysql    4u      REG              253,1         0     262237 /tmp/ibKN3LL5 (deleted)
mysqld    11819 11833        mysql    5u      REG              253,1         0     262239 /tmp/ibLy82XL (deleted)
mysqld    11819 11833        mysql    6u      REG              253,1         0     262240 /tmp/ibgXNkas (deleted)
mysqld    11819 11833        mysql    7u      REG              253,1         0     262242 /tmp/ibrNo5EO (deleted)
mysqld    11819 11833        mysql   11u      REG              253,1         0     262249 /tmp/ib9Rfc0u (deleted)
mysqld    11819 11834        mysql    4u      REG              253,1         0     262237 /tmp/ibKN3LL5 (deleted)
mysqld    11819 11834        mysql    5u      REG              253,1         0     262239 /tmp/ibLy82XL (deleted)
mysqld    11819 11834        mysql    6u      REG              253,1         0     262240 /tmp/ibgXNkas (deleted)
mysqld    11819 11834        mysql    7u      REG              253,1         0     262242 /tmp/ibrNo5EO (deleted)
mysqld    11819 11834        mysql   11u      REG              253,1         0     262249 /tmp/ib9Rfc0u (deleted)
mysqld    11819 11835        mysql    4u      REG              253,1         0     262237 /tmp/ibKN3LL5 (deleted)
mysqld    11819 11835        mysql    5u      REG              253,1         0     262239 /tmp/ibLy82XL (deleted)
mysqld    11819 11835        mysql    6u      REG              253,1         0     262240 /tmp/ibgXNkas (deleted)
mysqld    11819 11835        mysql    7u      REG              253,1         0     262242 /tmp/ibrNo5EO (deleted)
mysqld    11819 11835        mysql   11u      REG              253,1         0     262249 /tmp/ib9Rfc0u (deleted)
mysqld    11819 11836        mysql    4u      REG              253,1         0     262237 /tmp/ibKN3LL5 (deleted)
mysqld    11819 11836        mysql    5u      REG              253,1         0     262239 /tmp/ibLy82XL (deleted)
mysqld    11819 11836        mysql    6u      REG              253,1         0     262240 /tmp/ibgXNkas (deleted)
mysqld    11819 11836        mysql    7u      REG              253,1         0     262242 /tmp/ibrNo5EO (deleted)
mysqld    11819 11836        mysql   11u      REG              253,1         0     262249 /tmp/ib9Rfc0u (deleted)
mysqld    11819 11837        mysql    4u      REG              253,1         0     262237 /tmp/ibKN3LL5 (deleted)
mysqld    11819 11837        mysql    5u      REG              253,1         0     262239 /tmp/ibLy82XL (deleted)
mysqld    11819 11837        mysql    6u      REG              253,1         0     262240 /tmp/ibgXNkas (deleted)
mysqld    11819 11837        mysql    7u      REG              253,1         0     262242 /tmp/ibrNo5EO (deleted)
mysqld    11819 11837        mysql   11u      REG              253,1         0     262249 /tmp/ib9Rfc0u (deleted)
mysqld    11819 11838        mysql    4u      REG              253,1         0     262237 /tmp/ibKN3LL5 (deleted)
mysqld    11819 11838        mysql    5u      REG              253,1         0     262239 /tmp/ibLy82XL (deleted)
mysqld    11819 11838        mysql    6u      REG              253,1         0     262240 /tmp/ibgXNkas (deleted)
mysqld    11819 11838        mysql    7u      REG              253,1         0     262242 /tmp/ibrNo5EO (deleted)
mysqld    11819 11838        mysql   11u      REG              253,1         0     262249 /tmp/ib9Rfc0u (deleted)
mysqld    11819 11839        mysql    4u      REG              253,1         0     262237 /tmp/ibKN3LL5 (deleted)
mysqld    11819 11839        mysql    5u      REG              253,1         0     262239 /tmp/ibLy82XL (deleted)
mysqld    11819 11839        mysql    6u      REG              253,1         0     262240 /tmp/ibgXNkas (deleted)
mysqld    11819 11839        mysql    7u      REG              253,1         0     262242 /tmp/ibrNo5EO (deleted)
mysqld    11819 11839        mysql   11u      REG              253,1         0     262249 /tmp/ib9Rfc0u (deleted)
mysqld    11819 11840        mysql    4u      REG              253,1         0     262237 /tmp/ibKN3LL5 (deleted)
mysqld    11819 11840        mysql    5u      REG              253,1         0     262239 /tmp/ibLy82XL (deleted)
mysqld    11819 11840        mysql    6u      REG              253,1         0     262240 /tmp/ibgXNkas (deleted)
mysqld    11819 11840        mysql    7u      REG              253,1         0     262242 /tmp/ibrNo5EO (deleted)
mysqld    11819 11840        mysql   11u      REG              253,1         0     262249 /tmp/ib9Rfc0u (deleted)
mysqld    11819 11842        mysql    4u      REG              253,1         0     262237 /tmp/ibKN3LL5 (deleted)
mysqld    11819 11842        mysql    5u      REG              253,1         0     262239 /tmp/ibLy82XL (deleted)
mysqld    11819 11842        mysql    6u      REG              253,1         0     262240 /tmp/ibgXNkas (deleted)
mysqld    11819 11842        mysql    7u      REG              253,1         0     262242 /tmp/ibrNo5EO (deleted)
mysqld    11819 11842        mysql   11u      REG              253,1         0     262249 /tmp/ib9Rfc0u (deleted)
mysqld    11819 11843        mysql    4u      REG              253,1         0     262237 /tmp/ibKN3LL5 (deleted)
mysqld    11819 11843        mysql    5u      REG              253,1         0     262239 /tmp/ibLy82XL (deleted)
mysqld    11819 11843        mysql    6u      REG              253,1         0     262240 /tmp/ibgXNkas (deleted)
mysqld    11819 11843        mysql    7u      REG              253,1         0     262242 /tmp/ibrNo5EO (deleted)
mysqld    11819 11843        mysql   11u      REG              253,1         0     262249 /tmp/ib9Rfc0u (deleted)
mysqld    11819 11844        mysql    4u      REG              253,1         0     262237 /tmp/ibKN3LL5 (deleted)
mysqld    11819 11844        mysql    5u      REG              253,1         0     262239 /tmp/ibLy82XL (deleted)
mysqld    11819 11844        mysql    6u      REG              253,1         0     262240 /tmp/ibgXNkas (deleted)
mysqld    11819 11844        mysql    7u      REG              253,1         0     262242 /tmp/ibrNo5EO (deleted)
mysqld    11819 11844        mysql   11u      REG              253,1         0     262249 /tmp/ib9Rfc0u (deleted)
mysqld    11819 11845        mysql    4u      REG              253,1         0     262237 /tmp/ibKN3LL5 (deleted)
mysqld    11819 11845        mysql    5u      REG              253,1         0     262239 /tmp/ibLy82XL (deleted)
mysqld    11819 11845        mysql    6u      REG              253,1         0     262240 /tmp/ibgXNkas (deleted)
mysqld    11819 11845        mysql    7u      REG              253,1         0     262242 /tmp/ibrNo5EO (deleted)
mysqld    11819 11845        mysql   11u      REG              253,1         0     262249 /tmp/ib9Rfc0u (deleted)
mysqld    11819 11884        mysql    4u      REG              253,1         0     262237 /tmp/ibKN3LL5 (deleted)
mysqld    11819 11884        mysql    5u      REG              253,1         0     262239 /tmp/ibLy82XL (deleted)
mysqld    11819 11884        mysql    6u      REG              253,1         0     262240 /tmp/ibgXNkas (deleted)
mysqld    11819 11884        mysql    7u      REG              253,1         0     262242 /tmp/ibrNo5EO (deleted)
mysqld    11819 11884        mysql   11u      REG              253,1         0     262249 /tmp/ib9Rfc0u (deleted)
mysqld    11819 11904        mysql    4u      REG              253,1         0     262237 /tmp/ibKN3LL5 (deleted)
mysqld    11819 11904        mysql    5u      REG              253,1         0     262239 /tmp/ibLy82XL (deleted)
mysqld    11819 11904        mysql    6u      REG              253,1         0     262240 /tmp/ibgXNkas (deleted)
mysqld    11819 11904        mysql    7u      REG              253,1         0     262242 /tmp/ibrNo5EO (deleted)
mysqld    11819 11904        mysql   11u      REG              253,1         0     262249 /tmp/ib9Rfc0u (deleted)
mysqld    11819 11935        mysql    4u      REG              253,1         0     262237 /tmp/ibKN3LL5 (deleted)
mysqld    11819 11935        mysql    5u      REG              253,1         0     262239 /tmp/ibLy82XL (deleted)
mysqld    11819 11935        mysql    6u      REG              253,1         0     262240 /tmp/ibgXNkas (deleted)
mysqld    11819 11935        mysql    7u      REG              253,1         0     262242 /tmp/ibrNo5EO (deleted)
mysqld    11819 11935        mysql   11u      REG              253,1         0     262249 /tmp/ib9Rfc0u (deleted)
/usr/sbin 12642               root   18w      REG               0,19         0    7578555 /run/lock/apache2/authdigest-client.12642 (deleted)
/usr/sbin 12642               root   19w      REG               0,19         0    7578524 /run/lock/apache2/ssl-cache.12641 (deleted)
/usr/sbin 12642               root   20w      REG               0,19         0    7578556 /run/lock/apache2/authdigest-opaque.12642 (deleted)
/usr/sbin 12642               root   21w      REG               0,19         0    7578558 /run/lock/apache2/fcgid-proctbl.12642 (deleted)
/usr/sbin 12642               root   26w      REG               0,19         0    7578561 /run/lock/apache2/fcgid-pipe.12642 (deleted)
/usr/sbin 12642               root   27u      REG              253,1         0     262251 /tmp/.ZendSem.WilGzP (deleted)
/usr/sbin 12642               root   28w      REG               0,19         0    7578566 /run/lock/apache2/rewrite-map.12642 (deleted)
/usr/sbin 12642               root   29w      REG               0,19         0    7578569 /run/lock/apache2/mpm-accept.12642 (deleted)
/usr/sbin 12645           www-data   18w      REG               0,19         0    7578555 /run/lock/apache2/authdigest-client.12642 (deleted)
/usr/sbin 12645           www-data   19w      REG               0,19         0    7578524 /run/lock/apache2/ssl-cache.12641 (deleted)
/usr/sbin 12645           www-data   20w      REG               0,19         0    7578556 /run/lock/apache2/authdigest-opaque.12642 (deleted)
/usr/sbin 12645           www-data   21w      REG               0,19         0    7578558 /run/lock/apache2/fcgid-proctbl.12642 (deleted)
/usr/sbin 12645           www-data   26w      REG               0,19         0    7578561 /run/lock/apache2/fcgid-pipe.12642 (deleted)
/usr/sbin 12647           www-data   18w      REG               0,19         0    7578555 /run/lock/apache2/authdigest-client.12642 (deleted)
/usr/sbin 12647           www-data   19w      REG               0,19         0    7578524 /run/lock/apache2/ssl-cache.12641 (deleted)
/usr/sbin 12647           www-data   20w      REG               0,19         0    7578556 /run/lock/apache2/authdigest-opaque.12642 (deleted)
/usr/sbin 12647           www-data   21w      REG               0,19         0    7578558 /run/lock/apache2/fcgid-proctbl.12642 (deleted)
/usr/sbin 12647           www-data   26w      REG               0,19         0    7578561 /run/lock/apache2/fcgid-pipe.12642 (deleted)
/usr/sbin 12647           www-data   27u      REG              253,1         0     262251 /tmp/.ZendSem.WilGzP (deleted)
/usr/sbin 12647           www-data   28w      REG               0,19         0    7578566 /run/lock/apache2/rewrite-map.12642 (deleted)
/usr/sbin 12647           www-data   29wW     REG               0,19         0    7578569 /run/lock/apache2/mpm-accept.12642 (deleted)
/usr/sbin 12648           www-data   18w      REG               0,19         0    7578555 /run/lock/apache2/authdigest-client.12642 (deleted)
/usr/sbin 12648           www-data   19w      REG               0,19         0    7578524 /run/lock/apache2/ssl-cache.12641 (deleted)
/usr/sbin 12648           www-data   20w      REG               0,19         0    7578556 /run/lock/apache2/authdigest-opaque.12642 (deleted)
/usr/sbin 12648           www-data   21w      REG               0,19         0    7578558 /run/lock/apache2/fcgid-proctbl.12642 (deleted)
/usr/sbin 12648           www-data   26w      REG               0,19         0    7578561 /run/lock/apache2/fcgid-pipe.12642 (deleted)
/usr/sbin 12648           www-data   27u      REG              253,1         0     262251 /tmp/.ZendSem.WilGzP (deleted)
/usr/sbin 12648           www-data   28w      REG               0,19         0    7578566 /run/lock/apache2/rewrite-map.12642 (deleted)
/usr/sbin 12648           www-data   29w      REG               0,19         0    7578569 /run/lock/apache2/mpm-accept.12642 (deleted)
/usr/sbin 12649           www-data   18w      REG               0,19         0    7578555 /run/lock/apache2/authdigest-client.12642 (deleted)
/usr/sbin 12649           www-data   19w      REG               0,19         0    7578524 /run/lock/apache2/ssl-cache.12641 (deleted)
/usr/sbin 12649           www-data   20w      REG               0,19         0    7578556 /run/lock/apache2/authdigest-opaque.12642 (deleted)
/usr/sbin 12649           www-data   21w      REG               0,19         0    7578558 /run/lock/apache2/fcgid-proctbl.12642 (deleted)
/usr/sbin 12649           www-data   26w      REG               0,19         0    7578561 /run/lock/apache2/fcgid-pipe.12642 (deleted)
/usr/sbin 12649           www-data   27u      REG              253,1         0     262251 /tmp/.ZendSem.WilGzP (deleted)
/usr/sbin 12649           www-data   28w      REG               0,19         0    7578566 /run/lock/apache2/rewrite-map.12642 (deleted)
/usr/sbin 12649           www-data   29w      REG               0,19         0    7578569 /run/lock/apache2/mpm-accept.12642 (deleted)
/usr/sbin 12650           www-data   18w      REG               0,19         0    7578555 /run/lock/apache2/authdigest-client.12642 (deleted)
/usr/sbin 12650           www-data   19w      REG               0,19         0    7578524 /run/lock/apache2/ssl-cache.12641 (deleted)
/usr/sbin 12650           www-data   20w      REG               0,19         0    7578556 /run/lock/apache2/authdigest-opaque.12642 (deleted)
/usr/sbin 12650           www-data   21w      REG               0,19         0    7578558 /run/lock/apache2/fcgid-proctbl.12642 (deleted)
/usr/sbin 12650           www-data   26w      REG               0,19         0    7578561 /run/lock/apache2/fcgid-pipe.12642 (deleted)
/usr/sbin 12650           www-data   27u      REG              253,1         0     262251 /tmp/.ZendSem.WilGzP (deleted)
/usr/sbin 12650           www-data   28w      REG               0,19         0    7578566 /run/lock/apache2/rewrite-map.12642 (deleted)
/usr/sbin 12650           www-data   29w      REG               0,19         0    7578569 /run/lock/apache2/mpm-accept.12642 (deleted)
/usr/sbin 12651           www-data   18w      REG               0,19         0    7578555 /run/lock/apache2/authdigest-client.12642 (deleted)
/usr/sbin 12651           www-data   19w      REG               0,19         0    7578524 /run/lock/apache2/ssl-cache.12641 (deleted)
/usr/sbin 12651           www-data   20w      REG               0,19         0    7578556 /run/lock/apache2/authdigest-opaque.12642 (deleted)
/usr/sbin 12651           www-data   21w      REG               0,19         0    7578558 /run/lock/apache2/fcgid-proctbl.12642 (deleted)
/usr/sbin 12651           www-data   26w      REG               0,19         0    7578561 /run/lock/apache2/fcgid-pipe.12642 (deleted)
/usr/sbin 12651           www-data   27u      REG              253,1         0     262251 /tmp/.ZendSem.WilGzP (deleted)
/usr/sbin 12651           www-data   28w      REG               0,19         0    7578566 /run/lock/apache2/rewrite-map.12642 (deleted)
/usr/sbin 12651           www-data   29w      REG               0,19         0    7578569 /run/lock/apache2/mpm-accept.12642 (deleted)
```



[size=5]Background[/SIZE]

Last night, I had a huge problem.  My backup server said its disk was full, even though df was saying that 35% was available.  I am not certain, but I got the impression from research the problem was open deleted files.  I could not figure out how to release the space, so I blew that server away and rebuilt a new backup server.  I am now trying to figure out if I am having a problem with deleted open files on all 7 ubuntu servers I run.  All are 14.04.

---

### Post by Bucky Ball on 2015-11-02
*Thread moved to **Server Platforms**.*

---

### Post by tgalati4 on 2015-11-02
Garbage collection can be an issue.  What were the loads (*top*, *htop*) during this episode?  The system was showing 35% free, but perhaps it was too busy to update it.  How many processes?  When you hit 4,000 or so, bad things start to happen.  Web-based applications tend to spawn a lot of threads, so keep an eye on your thread-counts.  I treat log files as suggestions, not absolutes.  A failing disk can cause IO WAITs which can cause all sorts of problems.  What were your IO WAITs?

---

### Post by Dan_Allen on 2015-11-02
Thank you for picking this up.  i don't know the answer almost all your questions, but I think if I tell you what I was doing on that server, you might have good guesses.  That server was for backups of 7 other servers.  The backups were being made using rsync -a with --exclude clauses The backups were running hourly, making hourly snapshots, using script like this     mv /var/www/html/backups/bob/backup.24  /var/www/html/backups/bob/backup.daily.00   mv /var/www/html/backups/bob/backup.23  /var/www/html/backups/bob/backup.24 mv /var/www/html/backups/bob/backup.22 /var/www/html/backups/bob/backup.23  mv /var/www/html/backups/bob/backup.21 /var/www/html/backups/bob/backup.22  mv /var/www/html/backups/bob/backup.20 /var/www/html/backups/bob/backup.21     . . .  mv /var/www/html/backups/bob/backup.02 /var/www/html/backups/bob/backup.03  mv /var/www/html/backups/bob/backup.01 /var/www/html/backups/bob/backup.02   cp -al /var/www/html/backups/bob/backup.00  /var/www/html/backups/bob/backup.01  rsync -a --delete --log-file=/root/logs/rsync_bob.log  --exclude='www/vhosts/hwc.hwc.com/logs'  --exclude='www/vhosts/hwc.hwc.com/httpdocs/dbadm$  [/code]  Does that help figure out what is going on?  p.s. how do you get the code tags so show line breaks,?

---

### Post by SeijiSensei on 2015-11-02
If this problem persists, perhaps you should schedule a daily or more frequent mysql restart via cron.

---

### Post by tgalati4 on 2015-11-02
Your script works fine, until the time to perform a backup takes more than 1 hour, then you have overlapping *rsync* processes and ballooning worker threads.  Run *top* during a typical workday and watch for IO Waits (wa).  Set your interval to 3 hours.

---

### Post by Bucky Ball on 2015-11-02
To help your cause, please post terminal stuff between code tags (see last link in my signature). Post #4 is pretty much an unreadable wall of text. Code tags keep the formatting and make it readable. Thanks.

---

### Post by b-dan-w on 2015-11-17
I am Dan Allen, the thread starter.  I don't how I ended up with this account.  I will deal with straightening out my account later.

In the meantime, I really appreciate the tips posted. here.  I was wondering why seeing backups containing other backups on the inside.  I think the suggestion hourly jobs taking longer than an hour is pretty good guess of what the problem is.

There are a lot of other very thoughtful suggestions in here in addition to that one.  You guys are a real life line, thank you

---

### Post by b-dan-w on 2015-11-17
So I am going to try running every 3 hours instead of one.    

However, now I have  ton space I can't use, again.   How do I get it back?  Actually, how do I even verify that is the problem? 

Here is what I got, was trying open crontab
```
15-11-17 10:36:04 cron$ crontab -e
/tmp/crontab.WGwilb/crontab: No space left on device
Creation of temporary crontab file failed - aborting

```


This is the output from lsof|grep delete

```
init          1           root   12w      REG              253,1       68       5470 /var/log/upstart/systemd-logind.log.1 (deleted)
apache2    6010           root    9u      REG              253,1        0        211 /tmp/.ZendSem.rC00im (deleted)
apache2    6010           root   10w      REG               0,19        0     651376 /run/lock/apache2/mpm-accept.6010 (deleted)
apache2   13780       www-data    9u      REG              253,1        0        211 /tmp/.ZendSem.rC00im (deleted)
apache2   13780       www-data   10w      REG               0,19        0     651376 /run/lock/apache2/mpm-accept.6010 (deleted)
apache2   13782       www-data    9u      REG              253,1        0        211 /tmp/.ZendSem.rC00im (deleted)
apache2   13782       www-data   10w      REG               0,19        0     651376 /run/lock/apache2/mpm-accept.6010 (deleted)
apache2   30196       www-data    9u      REG              253,1        0        211 /tmp/.ZendSem.rC00im (deleted)
apache2   30196       www-data   10w      REG               0,19        0     651376 /run/lock/apache2/mpm-accept.6010 (deleted)
apache2   30200       www-data    9u      REG              253,1        0        211 /tmp/.ZendSem.rC00im (deleted)
apache2   30200       www-data   10w      REG               0,19        0     651376 /run/lock/apache2/mpm-accept.6010 (deleted)
apache2   30203       www-data    9u      REG              253,1        0        211 /tmp/.ZendSem.rC00im (deleted)
apache2   30203       www-data   10w      REG               0,19        0     651376 /run/lock/apache2/mpm-accept.6010 (deleted)
apache2   30204       www-data    9u      REG              253,1        0        211 /tmp/.ZendSem.rC00im (deleted)
apache2   30204       www-data   10w      REG               0,19        0     651376 /run/lock/apache2/mpm-accept.6010 (deleted)
apache2   30211       www-data    9u      REG              253,1        0        211 /tmp/.ZendSem.rC00im (deleted)
apache2   30211       www-data   10w      REG               0,19        0     651376 /run/lock/apache2/mpm-accept.6010 (deleted)
apache2   30215       www-data    9u      REG              253,1        0        211 /tmp/.ZendSem.rC00im (deleted)
apache2   30215       www-data   10w      REG               0,19        0     651376 /run/lock/apache2/mpm-accept.6010 (deleted)
apache2   30229       www-data    9u      REG              253,1        0        211 /tmp/.ZendSem.rC00im (deleted)
apache2   30229       www-data   10w      REG               0,19        0     651376 /run/lock/apache2/mpm-accept.6010 (deleted)
apache2   30234       www-data    9u      REG              253,1        0        211 /tmp/.ZendSem.rC00im (deleted)
apache2   30234       www-data   10w      REG               0,19        0     651376 /run/lock/apache2/mpm-accept.6010 (deleted)
root
```

```
/dev/vda1      408687024 185922992 201986532  48% /
none                   4         0         4   0% /sys/fs/cgroup
udev             2009900         4   2009896   1% /dev
tmpfs             404152       400    403752   1% /run
none                5120         0      5120   0% /run/lock
none             2020756         0   2020756   0% /run/shm
none              102400         0    102400   0% /run/user
```

---

### Post by tgalati4 on 2015-11-17
When you run out of space, bad things happen.  If you have backups inside of backups, then perhaps you have a nested directory that is getting backed up recursively.  Any /etc/fstab, SAMBA, or network mounts included in your backup directory tree?

---

