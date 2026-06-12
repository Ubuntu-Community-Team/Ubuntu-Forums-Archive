---
title: "session opened for user root by (uid=0)"
date: 2009-03-25
forum: Server Platforms
---

### Post by infinitezero on 2009-03-25
I always see the following line in my auth.log, any idea what it is?

pam_unix(cron:session): session opened for user root by (uid=0)


Thanks,
iz

---

### Post by BkkBonanza on 2009-03-26
That is likely cron running a task as root. 
You'd have to check the root crontab or the several /etc/cron.* directories to see what crons may be running.

To see the root crontab type,

sudo crontab -u root -l

but unless you set some up there is likely none and the cron you are seeing is from /etc/cron.daily or scripts in similar directories.

---

### Post by infinitezero on 2009-03-26
Thank you for the info, I appreciate it.


iz

---

