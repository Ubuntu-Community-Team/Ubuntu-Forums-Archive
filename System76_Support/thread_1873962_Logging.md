---
title: "Logging"
date: 2011-11-02
forum: System76 Support
---

### Post by lordbah on 2011-11-02
This is my first System76 system and my first experience with Ubuntu 11.10, so I don't really know which of my experiences are typical and which are not. Anyway here's a minor one, maybe it will help someone else ...

I found it odd that there was never anything in /var/log/syslog or auth.log. Turned out the problem was those files were owned by user 'colord' instead of root or syslog. How this happened I have no idea - I don't know what process they go through when they install these systems.

sudo chown syslog auth.log syslog

has fixed the problem.

---

### Post by isantop on 2011-11-03
Definitely aytpical there. It's good you got it fixed though, and I'll keep your solution in mind for future reference.

---

### Post by bluesloth on 2011-11-15
Logging works intermittently on my Gazelle with Oneiric I ordered October 12.
```
bluesloth@piedra:/var/log$ la -l | grep colord
-rw-r----- 1 colord            adm        0 2011-10-24 21:23 auth.log
-rw-r----- 1 colord            adm     6674 2011-10-17 07:46 auth.log.1
-rw-r----- 1 colord            adm        0 2011-11-02 18:21 kern.log
-rw-r----- 1 colord            adm    95128 2011-11-02 18:05 kern.log.1
-rw-r----- 1 colord            adm    70880 2011-10-17 07:46 kern.log.2.gz
-rw-r----- 1 colord            adm        0 2011-10-13 16:32 mail.err
-rw-r----- 1 colord            adm        0 2011-10-13 16:32 mail.log
-rw-r----- 1 colord            adm   381268 2011-11-15 17:21 syslog
-rw-r----- 1 colord            adm   116211 2011-11-15 10:21 syslog.1
-rw-r----- 1 colord            adm    21706 2011-11-02 18:21 syslog.2.gz
-rw-r----- 1 colord            adm    22422 2011-11-01 15:00 syslog.3.gz
-rw-r----- 1 colord            adm    31611 2011-10-29 03:26 syslog.4.gz
-rw-r----- 1 colord            adm    21616 2011-10-25 11:23 syslog.5.gz
-rw-r----- 1 colord            adm   109345 2011-10-19 10:05 syslog.6.gz
-rw-r----- 1 colord            adm        0 2011-10-13 16:32 ufw.log
```Weird.

I also had to fix the permissions on /var/lib/lightdm to get lightdm to start (looks like [bug 877066]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/877066")).

EDIT:  found 4 more..
```
bluesloth@piedra:/var/log$ sudo find . -user colord
./installer/syslog
./news/news.crit
./news/news.notice
./news/news.err
```

---

