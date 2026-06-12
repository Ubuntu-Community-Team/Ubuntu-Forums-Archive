---
title: "Cron not working!"
date: 2011-01-24
forum: Server Platforms
---

### Post by papamike3108 on 2011-01-24
Hi, I have this line in my crontab, the command work when executed in shell, but not in the cron. Someone can help?
Thanks!
Pascal

```
* * * * *       mysqldump --host=localhost --user=root --password=******* cedule > /home/****/public_html/cedule/backup/cedule_`date +%F`.sql
```

---

### Post by ajgreeny on 2011-01-24
If I assume **mysqldump** is the executable of the command, use its full path eg **/usr/bin/mysqldump** or wherever it resides in your filesystem.

Cron uses a reduced, customised version of bash with limited PATH variables so full pathways are usually needed.

---

### Post by psusi on 2011-01-24
You also did not specify any time when it should run.

---

### Post by papamike3108 on 2011-01-24
> **psusi said:**
> You also did not specify any time when it should run.
It's only for testing purpose. I want it to happen every minutes.. Isn't it the good way to do it?

But it still doesn't work, even with full path.

---

### Post by DaithiF on 2011-01-24
The '%' character is special to cron -- it denotes the end of a command, the remaining piece being treated as a comment.

So one problem is that your date command will get cut in two, likely leading to a unmatched backtick error.

More generally, if your cron command is anything more complicated that a simple command invocation, then put the command in a script, and run that script from cron instead.

Secondly, log output from your script so that you can debug errors.

so in short, put your command into a script, and invoke the script from cron something like:
```
* * * * * /path/to/script &> /path/to/logfile

```

---

### Post by papamike3108 on 2011-01-25
It works! Thanks. The only weird thing: I'm not able to write anything in the log. I tried a echo in the script, but nothing was working.

---

