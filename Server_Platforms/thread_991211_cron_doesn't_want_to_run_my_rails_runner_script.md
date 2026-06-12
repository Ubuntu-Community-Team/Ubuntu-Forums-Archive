---
title: "cron doesn't want to run my rails runner script"
date: 2008-11-23
forum: Server Platforms
---

### Post by dalison on 2008-11-23
My ISP has provided me with a virtual server that is running Ubuntu 8.04.1. It is currently hosting my Rails based application. Everything works fine for my web based application. I can also fire up the script/console for my application just fine.

The problem is when I try to use the script/runner capabilities of rails in a cron job. If I manually run the script everything works fine, however if the script runs through cron it doesn't actually execute the rails script.

I've packaged up the call to the runner script in a bash shell script. If I take a look at the syslog I can see that it actually executed the underlying bash shell script that in turn calls the rails runner script.

I could really use some advice for how to troubleshoot this. I've searched the interwebs to no avail. Are there settings for cron that would limit the ability for this to execute properly? If I run top on my server instance this is what I get:

Mem:    786432k total,   197396k used,   589036k free, 

Should be plenty of memory to run this. Any pointers to how to troubleshoot this is greatly appreciated.

---

### Post by pdwerryhouse on 2008-11-23
Could be a PATH issue ... cron might only be running your script with a PATH of /usr/bin:/bin

---

### Post by dalison on 2008-11-23
> **pdwerryhouse said:**
> Could be a PATH issue ... cron might only be running your script with a PATH of /usr/bin:/bin

Thanks for the reply but nope, not a path issue. My cron file has the script being called out explicitly.

---

### Post by dalison on 2008-11-23
OK, I was running this in a user's crontab. I changed the script to be called from the main crontab (/etc/crontab) and now it appears to be working properly. Really odd error but hopefully if someone else encounters this problem they can try using the system crontab and see if it solves the problem. I'd still love to know what was causing it though. :confused:

---

