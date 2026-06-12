---
title: "lftp"
date: 2011-09-15
forum: Server Platforms
---

### Post by atwright on 2011-09-15
Hi,

I am actually working with a CentOS 5 VPS and I have just installed lftp to help me backup to LiveDrive.com

I have installed it successfully and connected to the destination server.

I want to run the backup between 7pm and 8am. Therefore, I need a way to ensure that the backup stops at 8am. How would I do this with Cron?

Many thanks,


Andy

---

### Post by zackwasa on 2011-09-15
You can set up a separate cron at 8am which checks if the backup cron is still running and kills it if it is

---

### Post by demonipuch on 2011-09-15
Hi atwright

```
0 0-8,19-23 * * * your_command
```
Not sure if it's what you're looking for but this cronjob will run "your_command" every hour between 7pm and 8am.

---

