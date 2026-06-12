---
title: "Cron job creates random dated log files, how to have those logs emailed after it runs"
date: 2012-01-03
forum: Server Platforms
---

### Post by Gizim on 2012-01-03
I have two cron jobs that run one of them is at noon and at midnight it will do a rsync from our mail server to a NAS. It will create a log filed based on the year, month and date it was ran. The second runs every Sunday at 4am it is a full backup of the email server and database and then also rsyncs it as well as creates the same type of log.

Is there a way I can run into the job that when it completes it will attach that log file that was just created and email it off to [email]myname@domain.com[/email] ?

---

### Post by HugoSerrano on 2012-01-04
add:
MAILTO=[EMAIL="myname@domain.com"]myname@domain.com[/EMAIL]

to crontab. I usual put it on top, first line.
eg:

```

MAILTO=[EMAIL="myname@domain.com"]myname@domain.com[/EMAIL]

* * * * * echo "Ubuntu Rules"

```

Best Regards.

---

