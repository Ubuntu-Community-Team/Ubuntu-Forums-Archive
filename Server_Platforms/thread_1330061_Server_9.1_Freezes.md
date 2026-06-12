---
title: "Server 9.1 Freezes"
date: 2009-11-18
forum: Server Platforms
---

### Post by ask21900 on 2009-11-18
My install of 9.1 has been freezing consistently today.  After an extensive search of all log files (that I could find anyway) I have concluded that about 95% of the freezes came after a cron running.

There were a few different crons that may be the culprit:

```
Nov 17 20:39:01 server1 CRON[1728]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
```

and

```
Nov 17 21:17:01 server1 CRON[1467]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

both have been the last log entry before the system freezes several times.

There have been other crons ran successfully in between these freezes.


I am fairly new to Ubuntu server administration and would appreciate any insight anybody can give me to get this resolved.

Thanks in advance!

---

### Post by ask21900 on 2009-11-19
bump.  Nobody has any idea what might be going on here?  Please help!!

---

### Post by L33tCh on 2009-11-19
Ever since upgrade to 9.10 I also get the freezing after about 10 mins... logs don't show anything interesting tho... all appears correct, but had no problem till now :(

---

### Post by _Smiley_ on 2010-02-16
Perhaps the answer can be found here: [http://serverfault.com/questions/80520/ubuntu-server-9-10-freezes-up-after-10-minutes](http://serverfault.com/questions/80520/ubuntu-server-9-10-freezes-up-after-10-minutes)

---

