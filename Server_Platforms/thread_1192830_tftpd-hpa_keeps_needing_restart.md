---
title: "tftpd-hpa keeps needing restart"
date: 2009-06-20
forum: Server Platforms
---

### Post by sherl0k on 2009-06-20
I'm having trouble with tftpd-hpa and xinetd. The service will work for a little while for PXE booting, but it will stop after maybe a halfhour or so. I restart xinetd and it kicks right back on.

I edited crontab so it would restart on its own every 5 minutes but I don't think it's working. Is this right?

```
*/5 * * * * /etc/init.d/xinetd restart
```

If not, do I need to write a bash script to restart it instead of directly calling it?

---

### Post by windependence on 2009-06-21
Have you checked your logs to see why this is happening? Check /var/log/messages.

-Tim

---

### Post by sherl0k on 2009-06-21
Hm, no... I just kept looking at /var/log/syslog. I'll check messages tomorrow to see if it says anything.

---

### Post by sherl0k on 2009-06-22
Yeah I checked in there, no messages from xinetd or tftpd-hpa at all. The cron wasn't working either so I wrote a bash script to restart xinetd every 2 minutes. Crude, but it works.

---

