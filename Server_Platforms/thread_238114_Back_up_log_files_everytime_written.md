---
title: "Back up log files everytime written"
date: 2006-08-17
forum: Server Platforms
---

### Post by hagen00 on 2006-08-17
Hi there

I'm looking for a solution that will allow me to backup my log files onto a remote computer everytime they are written. 

I could probably run a cron every minute or so that runs rsync to see whether they've changed, but ideally I would want something that backs the log up just as it is written. 

Any ideas? I'm not concerned about the code for the backup scripts, just the best way to architect this. 

Thanks

H

---

### Post by Klaidas on 2006-08-17
Logs are writted about every few seconds, i guess.
No need to back them up every minute
Once a day is more than enough

---

### Post by hagen00 on 2006-08-17
How about the following scenario....you get hacked, they delete the logs and you don't know what happenend, since you only have the clean logs. 

That scenario unfortunately happenend with me today.

---

### Post by LordHunter317 on 2006-08-17
Setup syslog to log to another server.  The manpages have plenty of documentation on how to do this.

---

