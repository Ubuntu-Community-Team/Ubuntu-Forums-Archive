---
title: "Starting Multiple Programs at Boot on Server"
date: 2010-02-11
forum: Server Platforms
---

### Post by MickSulley on 2010-02-11
Running Ubuntu Server 9.10.

I have a couple of programs that I would like to start at boot, they will both run forever.  I have created a cron job with @reboot and that will start a program, but if I have multiple programs in there it waits for the first to finish before starting the next.

Is there any way to start multiple programs simultaneously?

Thanks
Mick

---

### Post by yogesh.girikumar on 2010-02-12
Hi,
       In the crontab file you can set them to execute simultaneously. This is done by starting an execution and pushing it to the background (thereby not waiting for it to complete) and then executing the second command.
       e.g.
   ```
17 *    * * *   root    service apache2 restart && service bluetooth restart
```will first start the restart of apache and then it'll wait till apache has been completely restarted and then moves on to the second command. Instead, you can do this:
```
17 *    * * *   root    service apache2 restart & service bluetooth restart
``` A single '&' instead of two will start the first service and push it to the background and starts the second service right away.
       Hope this helps.

---

### Post by Vishal Agarwal on 2010-02-12
If you want to start the jobs at the booting time then the /etc/rc.local is better option. Although you can do the same with crontab, but crontab is usually used for time bounded jobs.

rc.local executes every time once when the computer boots.

---

