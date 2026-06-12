---
title: "Crontab date issue"
date: 2010-12-09
forum: Server Platforms
---

### Post by smo0th on 2010-12-09
I have a process running every 30 minutes, it checks a file date using the info shown by 'ls -l' however when the process is ran by crontab, the date is shown as 'Dec 9' instead of '2010-12-09', any ideas on how to make it display the 'ls -l' date in the YYYY-MM-DD format?

---

### Post by amauk on 2010-12-09
See the man page for ls
you can specify exactly how the time is printed with "--time-style"

```
ls -l --time-style="+%Y-%m-%d"
```

---

### Post by 3L33T on 2010-12-09
> **smo0th said:**
> I have a process running every 30 minutes, it checks a file date using the info shown by 'ls -l' however when the process is ran by crontab, the date is shown as 'Dec 9' instead of '2010-12-09', any ideas on how to make it display the 'ls -l' date in the YYYY-MM-DD format?


Post your cron job please.

First convert the date format in your shell:

> 

export mydate=`date +%F`



---

### Post by smo0th on 2010-12-09
amauk, thanks, that made de job done, I'm ashamed you make me feel like a newbie 

3L33T, thanks, manually formating the ls time style worked pretty well

---

