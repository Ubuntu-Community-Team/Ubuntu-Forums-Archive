---
title: "Adjust system time -- problematic?"
date: 2008-06-04
forum: Server Platforms
---

### Post by lodp on 2008-06-04
I noticed that on my rented Ubuntu web server the clock runs 10 minutes ahead. It's not disruptive or anything, but it's a nuissance.

Is there a way to synchronize the time with a central source somehow? I know the GUI way to do this -- but how can I do this on  command line on my remote server?

Also, am I likely to run into any problems when setting the time back? Do I have to watch out for anything?

---

### Post by wdaniels on 2008-06-04
Try:

```
sudo ntpdate ntp.ubuntu.com
```

There shouldn't be any issues with moving it just ten minutes, or not that I can think of...

---

### Post by lodp on 2008-06-04
thanks! worked like a charm, and no problems so far..

i guess i'll run this on a cronjob, once a week or so.

---

### Post by koenn on 2008-06-04
> **lodp said:**
>  Do I have to watch out for anything?
Yes : lots of stuff is time related. That's why it's such a good idea to use time servers (ntp). some examples : changing the time back can have an effect on
- all log files that record the time an event occurred. 
- jobs that look at file modification times, such as most backup jobs
- some authentication schemes, such as Kerberos tickets
- cron jobs - soe jobs might run twice

10 minutes isn't that much, but you're log files may show events in a peculiar order, so if you happen to have a problem, using the log to diagnose it is going to be harder, stuff like that. Just something to keep in mind for the next couple of days.

---

### Post by lodp on 2008-06-04
> - all log files that record the time an event occurred.
- jobs that look at file modification times, such as most backup jobs
- some authentication schemes, such as Kerberos tickets
- cron jobs - soe jobs might run twice

Thanks for those .. i'll keep in mind the thing with the logs.

So far there's only one immediate problem that I noticed: fetching mails with POP3 didn't work any more. Turns out dovecot didn't like the time change:

quoting from /var/log/mail.log:

> 
Jun  4 15:22:46 host dovecot: Time just moved backwards by 614 seconds. This might cause a lot of problems, so I'll just kill myself now. [http://wiki.dovecot.org/TimeMovedBackwards](http://wiki.dovecot.org/TimeMovedBackwards)

I started dovecot and it's working now. What's weird is that a test message that I sent to one of my accounts before doing that didn't arrive. The message didn't bounce or anything, it just didn't get there. not showing up in the mail log either. I didn't think dovecot not running could be responsible for such a thing..

Edit: I found that there's actually a package called plainly ntp, which runs a daemon to keep the time in sync. Very nice.

---

### Post by koenn on 2008-06-04
I didn't think of mail handling, but I can sort of understand how timeouts and retry mechanisms may be affected, and I've seen other programs complain about having to handle files swith creation dates in the future, so the dovecot wiki page makes sense.
 
ntpd is definitely a good idea

---

