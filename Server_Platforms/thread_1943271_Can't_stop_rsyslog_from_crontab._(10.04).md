---
title: "Can't stop rsyslog from crontab. (10.04)"
date: 2012-03-19
forum: Server Platforms
---

### Post by SteveGodfrey on 2012-03-19
This should be very straight forward!

All I'm trying to do is restart rsyslog from crontab.

> 
10 11 * * * /etc/init.d/rsyslog stop
CRON[21475]: (root) CMD (/etc/init.d/rsyslog stop)


After this has run rsyslog is still running
> service rsyslog status
rsyslog start/running, process 21500


> 15 11 * * * /usr/sbin/rsyslog stop
CRON[21661]: (root) CMD (/usr/sbin/service rsyslog stop)


Same as before
> service rsyslog status
rsyslog start/running, process 21500


As you can see I've tried both ways to stop it, both word from the command line.

I've use the same crontab entry to stop Apache which works as expected so it would seem to be rsyslog related.

---

