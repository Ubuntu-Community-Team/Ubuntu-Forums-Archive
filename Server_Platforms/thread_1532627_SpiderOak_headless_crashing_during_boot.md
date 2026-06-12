---
title: "SpiderOak headless crashing? during boot"
date: 2010-07-16
forum: Server Platforms
---

### Post by ceallred on 2010-07-16
I have a cron job to start spideroak when the server boots
```
@reboot /usr/scripts/run_spideroak.sh > /var/log/SpiderOak.log 2>&1 &
```

Script is a wrapper for one command
```
#!/bin/bash
echo "Job Run At $(date)"
echo "===================="
echo "process list is $(ps -A|grep SpiderOak)"
echo "about to run spideroak"
/usr/bin/SpiderOak --headless &
echo "$(date) Spideroak launched."
echo " process list is $(ps -A|grep SpiderOak)"
echo "job finished"

```

Process is started and logfile generated, however by the time I can SSH into the box it has quit or crashed.  I have to start it again manually.

```
Job Run At Fri Jul 16 17:28:19 EDT 2010
====================
process list is 
about to run spideroak
Fri Jul 16 17:28:19 EDT 2010 Spideroak launched.
 process list is  1101 ?        00:00:00 SpiderOak
job finished
Command line arguments not allowed during New User Setup
``` 

Interestingly enough....  the line saying "Command line arguments not allowed during new user setup" isn't from my script.   Any chance that has something to do with it?

---

### Post by burnzy on 2010-09-17
I'm having the same issue. Did you ever solve this problem?

---

### Post by dreamie on 2010-10-21
Use this to start SpiderOak from crontab:
@reboot /sbin/start-stop-daemon -b -x /usr/bin/SpiderOak -S -- --headless

Regards,

 Peter

---

