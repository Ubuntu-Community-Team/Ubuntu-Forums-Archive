---
title: "delay service shutting down on reboot"
date: 2012-06-12
forum: Server Platforms
---

### Post by SlugSlug on 2012-06-12
I need to delay MySQL stopping on reboot, I have another service running that depends on it which takes around 30 seconds to completly shutdown.

Is there (am sure there is :) ) a way to make MySQL wait untill this other service has shut down before it it's self shuts down ?

---

### Post by LHammonds on 2012-06-12
I have a Minecraft server that runs in RAM but requires regular reboots.  In the crontab schedule, I call a reboot script rather than the reboot command.  The script then runs through the processes that need to happen in a particular order and reboot only once the service is shutdown and files have been copied to the HD.

You can make the script as complicated and robust as you like or as simple as you like.

For example, you could issue the service shutdown command, sleep for 60 seconds and then issue the "service mysql stop" command, wait a few seconds and then issue the reboot command.

Or you can issue the 1st service shutdown command and wait for 60 seconds and run a verification check to ensure that service has gone down...if not, wait some more and repeat check.  Then issue the MySQL shutdown command, wait and verify the service is stopped and then log the results and reboot the server.

LHammonds

---

### Post by SlugSlug on 2012-06-12
mine too is minecraft, is just some times I hit reboot and noticed it can roll back a bit

---

### Post by LHammonds on 2012-06-12
I'll post a link to my exact solution I have documented on the Minecraft forums (I think) and put the link in this post.

EDIT:
> **SlugSlug said:**
> cron job's not really a solution for me tbh, I  tend to just hit reboot as I work locally on the box too
Well, in that case, I'll move on since my solution would not work for you.

---

### Post by SlugSlug on 2012-06-12
cron job's not really a solution for me tbh, I tend to just hit reboot as I work locally on the box too

---

