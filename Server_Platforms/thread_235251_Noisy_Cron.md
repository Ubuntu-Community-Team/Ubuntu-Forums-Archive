---
title: "Noisy Cron"
date: 2006-08-12
forum: Server Platforms
---

### Post by voltagex on 2006-08-12
Hi
I'm running a script called moblock which is run daily by cron... the problem is that it generates a lot of output - seems to be >500k of text. 

I don't want to get rid of this script, just the output it generates.

I'm kinda confused here... which part of the crontab sends the email to the admin?

---

### Post by mannheim on 2006-08-12
I think that the way things are set up means that if a cron job like this one produces *any* output, it is mailed to root (and the mail system typically diverts root's mail to the first user created at installation time).

So the thing to do is to modify the script (moblock?) so that it doesn't write anything to stdout or stderr unless something fails. Redirect the output to a file.

---

### Post by n8bounds on 2006-08-12
> **voltagex said:**
> Hi
I'm running a script called moblock which is run daily by cron... the problem is that it generates a lot of output - seems to be >500k of text. 

I don't want to get rid of this script, just the output it generates.

I'm kinda confused here... which part of the crontab sends the email to the admin?


or in your crontab add > /dev/null to the tail of that line...

---

### Post by woifi on 2006-08-13
> **voltagex said:**
> Hi
I'm running a script called moblock which is run daily by cron... the problem is that it generates a lot of output - seems to be >500k of text. 

I don't want to get rid of this script, just the output it generates.

I'm kinda confused here... which part of the crontab sends the email to the admin?
```
/path/to/moblock > /dev/null 2>&1
```

hth

woifi

---

### Post by voltagex on 2006-08-15
Yep, that worked (I only redirected stdout). Thanks

---

