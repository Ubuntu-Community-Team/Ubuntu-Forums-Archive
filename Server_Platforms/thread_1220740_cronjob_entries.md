---
title: "cronjob entries"
date: 2009-07-23
forum: Server Platforms
---

### Post by Gorlist on 2009-07-23
Good day, having some problems with my crontab. Entered the following as root:

```
0 5 * * * rkhunter --cronjob --rwo | mail -s "Daily Rootkit Hunter Scan" admin@mydomain.co.uk
0 6 * * * /usr/sbin/chkrootkit; /usr/sbin/chkrootkit -q 2 >&1 | mail -s "Daily ChkRootKit Scan" admin@mydomain.co.uk
0 7 * * * unhide proc; unhide proc -q 2 >&1 | mail -s "Daily unhide proc Scan" admin@mydomain.co.uk
30 7 * * * unhide sys; unhide sys -q 2 >&1 | mail -s "Daily unhide sys Scan" admin@mydomain.co.uk
0 8 * * * unhide brute; unhide brute -q 2 >&1 | mail -s "Daily unhide brute Scan" admin@mydomain.co.uk
30 8 * * * unhide-tcp; unhide-tcp -q 2 >&1 | mail -s "Daily unhide-tcp Scan" admin@mydomain.co.uk
```

but they do not appear to be functioning. Where abouts could any errors be logged? syslog?

Best Regards

---

### Post by bacil on 2009-07-23
yes cron logs to /var/log/syslog

line should look like this 

```
Jul 22 20:17:01 one /USR/SBIN/CRON[11252]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

and your crontab looks healthy so it might be in the scripts you running or some parameters missing or some config error in mail system if you are not getting mails

---

### Post by Gorlist on 2009-07-29
Thanks for the reply, sorry for not getting back sooner - was waiting to see the results.

Right checking over the system log im getting the following:

```
Jul 29 16:57:01 sv1 CRON[9398]: User account has expired
```

None of my crons appear to be working (so nothing in the cron directory's, including root crontab).

Im wondering whether its caused due to how I installed Ubuntu, which was done remotely using the root user account, I later disabled (after completion) and moved over to sudo. 

Might also explain some other anomaly's ive been having? 

To note plesk however still excutes its own crons fine:

```
Jul 29 01:40:01 sv1 /USR/SBIN/CRON[30908]
```

Any suggestions or possible solutions?

Best Regards

---

### Post by Gorlist on 2009-07-30
Possible solution:

[http://ubuntuforums.org/showthread.php?t=1054283](http://ubuntuforums.org/showthread.php?t=1054283)

lets see if it works :)

---

### Post by Gorlist on 2009-07-31
Okay after re-enabling my root login the main root crontab has started to function - however the cron directory's are still inactive? (or atleast appear to be)

Im at a loss to explain it... help!

**Doh! I installed from minimal installation - anacrom. - possibly fixed.**

---

