---
title: "sendmail/postfix confusion"
date: 2006-05-04
forum: Server Platforms
---

### Post by abovett on 2006-05-04
Whilst trying to get mail to work in PHP, I initially installed sendmail, but then installed postfix instead. PHP is now sending mail OK, and apt says that sendmail isn't installed, but there's a cron job sending me error messages messages every 20 minutes which seem to relate to a broken sendmail installation, and /usr/bin/sendmail is still on my system.

Here's an example message:
```
Subject: Cron <smmsp@europa-dapper> test -x /usr/share/sendmail/sendmail && /usr/share/sendmail/sendmail cron-msp

/usr/share/sendmail/sendmail: line 826: /usr/sbin/sendmail-msp: No such file or directory

```

Anyone know what's going on here? I get the feeling that sendmail has not been properly removed. I'm running dapper - could it be a broken package or am I missing something?

Cheers

Andy B

---

### Post by abovett on 2006-05-10
I still haven't sorted this - does anyone have an answer?

---

### Post by soce_32 on 2006-05-10
You could try `aptitude purge sendmail`, which should remove all traces of sendmail.  You can also try checking in /etc/cron.* for leftover sendmail cron jobs or do something like `find /etc -depth -type f -exec grep -H sendmail {} \;`, which should turn up your offending cron job.

---

### Post by abovett on 2006-05-11
"aptitude purge sendmail" didn't work, but I've since realised that although the "sendmail" package had been removed, "sendmail-base" and "sendmail-cf" were still installed. I'll remove them and see what happens.

Of course, I could as you suggest just kill the cron job, but it's existence and the text in the message implied that things weren't quite right - I'd prefer to fix the problem rather than hiding the symptoms if possible!

Thanks for the help

Andy B

---

### Post by abovett on 2006-05-11
Well - removing the other sendmail packages has stopped the mail messges and removed the extra sendmail files, so I guess that was it. Problem solved.

Andy B

---

