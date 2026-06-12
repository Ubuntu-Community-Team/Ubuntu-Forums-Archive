---
title: "Crontab time + date stamp"
date: 2019-08-27
forum: Server Platforms
---

### Post by chrispet on 2019-08-27
Hi, i'm newbie so i want your help about crontab. Specially i want when the cron runs in generated tar.gz file as part of name file include the date and time. I tried with this command : 'date +%Y-%m-%d' but this includs only the full date. 

Thank you

---

### Post by TheFu on 2019-08-27
Every command on Unix has a manpage which explains the available options.
```
$ man date
```

I would probably use **date "+%F-%T"** , but I didn't check the manpage. There is probably a cleaner way.
It needs to be quoted as I've done so the shell doesn't interpret the formatting.

---

