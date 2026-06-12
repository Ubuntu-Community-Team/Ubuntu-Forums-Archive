---
title: "Strange date from the past in syslog"
date: 2015-02-27
forum: Server Platforms
---

### Post by hovis on 2015-02-27
Hello, has anyone ever seen the following behaviour in their syslog? (Ubuntu server 14.04 LTS)...

```

Feb 27 07:00:02 nas CRON[24766]: (root) CMD (if [ -x /usr/bin/mrtg ] && [ -r /etc/mrtg.cfg ] && [ -d "$(grep '^[[:space:]]*[^#]*[[:space:]]*WorkDir' /etc/mrtg.cfg | awk '{ print $NF }')" ]; then mkdir -p /var/log/mrtg ; env LANG=C /usr/bin/mrtg /etc/mrtg.cfg 2>&1 | tee -a /var/log/mrtg/mrtg.log ; fi)
Feb 27 07:02:01 nas CRON[24792]: (logcheck) CMD (   if [ -x /usr/sbin/logcheck ]; then nice -n10 /usr/sbin/logcheck; fi)
Feb 27 07:09:01 nas CRON[25866]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Feb 24 04:10:01 nas CRON[26096]: (root) CMD (if [ -x /usr/bin/mrtg ] && [ -r /etc/mrtg.cfg ] && [ -d "$(grep '^[[:space:]]*[^#]*[[:space:]]*WorkDir' /etc/mrtg.cfg | awk '{ print $NF }')" ]; then mkdir -p /var/log/mrtg ; env LANG=C /usr/bin/mrtg /etc/mrtg.cfg 2>&1 | tee -a /var/log/mrtg/mrtg.log ; fi)
Feb 27 07:10:01 nas CRON[26097]: (root) CMD (if [ -x /usr/bin/mrtg ] && [ -r /etc/mrtg.cfg ] && [ -d "$(grep '^[[:space:]]*[^#]*[[:space:]]*WorkDir' /etc/mrtg.cfg | awk '{ print $NF }')" ]; then mkdir -p /var/log/mrtg ; env LANG=C /usr/bin/mrtg /etc/mrtg.cfg 2>&1 | tee -a /var/log/mrtg/mrtg.log ; fi)
Feb 27 07:15:01 nas CRON[26140]: (root) CMD (if [ -x /usr/bin/mrtg ] && [ -r /etc/mrtg.cfg ] && [ -d "$(grep '^[[:space:]]*[^#]*[[:space:]]*WorkDir' /etc/mrtg.cfg | awk '{ print $NF }')" ]; then mkdir -p /var/log/mrtg ; env LANG=C /usr/bin/mrtg /etc/mrtg.cfg 2>&1 | tee -a /var/log/mrtg/mrtg.log ; fi)

```

Note the strange "Feb 24" date in amongst the usual suspects this morning (27th).

I have restarted both CRON and rsyslog and will see if it happens again.  Server is in the "Europe/London" timezone and also runs ntp.  It was recently upgraded from 12.04 LTS and was booted on the 5th Feb.

---

### Post by Doug S on 2015-02-27
Is the related entry for "Feb 24 04:10:01" missing from that area of the Feb 24th log?
I don't know for certain about syslog, but I do know for some other logs that the date and time stamp is for when the task started and the log entry is actually made when the task finished.
What I am suggesting is perhaps that job somehow took 3 days to complete.

Edit: Here is a not great example:```
access.log.5-50.31.96.9 - - [17/Jan/[COLOR=#ff0000]2015:19:36:08[/COLOR] -0800] "GET /xmas_2008/index.html HTTP/1.1" 200 2221 "-" "Java/1.6.0_23"
access.log.5:50.31.96.9 - - [17/Jan/2015:[COLOR=#ff0000]19:35:45[/COLOR] -0800] "GET /bot_trap.html HTTP/1.1" 200 599 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/39.0.2171.95 Safari/537.36"
```

---

### Post by hovis on 2015-02-27
Many thanks, it is missing from the logs from the 24th.

I think I have solved this now.  Another job in the crontab did 'hang' on the 24th at the same time (a backup script which executes at that time every night) which I assume then held up that particular mrtg job (and I guess any other cron jobs in the 'daily', 'weekly', 'monthly' folders).

---

