---
title: "cron sending email from address"
date: 2011-04-29
forum: Server Platforms
---

### Post by jbollom on 2011-04-29
Hey,

Can anyone tell me how i change the default domain name for cron?
everything i cron runs it emails from and to [email]user@com.com[/email]

this leaves me with a massive list of failed mails in postfix
i have mailto on my main crontab but i cant do it on all of them

Thanks,
Josh

---

### Post by falko on 2011-04-30
You can use the MAILTO command (see [http://www.howtoforge.com/a-short-introduction-to-cron-jobs](http://www.howtoforge.com/a-short-introduction-to-cron-jobs) ).

---

