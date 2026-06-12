---
title: "Suspicious Entry in Syslog"
date: 2010-02-28
forum: Security
---

### Post by waveslider on 2010-02-28
This morning after turning on my computer, I saw this is my system log file:

```
2010-02-28 08:09:01	Surfer	CRON[2890]	
(root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
```

I am only a level 1 shell user, so I am not very familiar with bash scripting syntax. My intuition tells me this cron job was probably created when I installed php5, but my paranoia compelled me to post this.

Can anyone tell me what this script does and why it would be in my cron?

Thanks!

---

### Post by Soul-Sing on 2010-02-28
This has something to do with networkshares: xargs -n 200 -r -0 rm
But the print option is not clear to me...:/

---

### Post by adam814 on 2010-03-02
That seems to be the case.  It finds regular files (not directories or special files) in the directory /var/lib/php5 that haven't been changed in longer than whatever /usr/lib/php5/maxlifetime returns (in my case 24) minutes ago and deletes them.

I'm not an expert with PHP or anything, but I'm guessing it's normal.  At least it isn't going to mess with anything outside your /var/lib/php5 directory.

---

### Post by FuturePilot on 2010-03-02
Yes, that's normal. It's a cron job /etc/cron.d/php5.

```
# /etc/cron.d/php5: crontab fragment for php5
#  This purges session files older than X, where X is defined in seconds
#  as the largest value of session.gc_maxlifetime from all your php.ini
#  files, or 24 minutes if not defined.  See /usr/lib/php5/maxlifetime

# Look for and purge old sessions every 30 minutes
09,39 *     * * *     root   [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm
```

---

### Post by waveslider on 2010-03-02
Oh cool, that is a relief. Thank you!

---

### Post by HotForLinux on 2010-05-23
Today I discovered the same thing. But the strange thing is that it is being done every half an hour. Why? The crontab doesn't show the task.

---

### Post by FuturePilot on 2010-05-23
> **HotForLinux said:**
> Today I discovered the same thing. But the strange thing is that it is being done every half an hour. Why? The crontab doesn't show the task.

It's not in crontab. See my post above. It's /etc/cron.d/php5

---

### Post by HotForLinux on 2010-05-24
> **FuturePilot said:**
> It's not in crontab. See my post above. It's /etc/cron.d/php5

Oh yes.. you are right. It is a cron job but not in the 'usual' crontab. I didn't know that existed.
I thought that file was just another shell script  executed by cron. But now I see that it is not a a shell script but a sort of crontab extension. Oh my....
Each time it is getting more complicated (or messy... i don't know). The file doesn't even have the headers for the tasks and they want to make Linux more accesible?

---

