---
title: "cron.daily logrotate error"
date: 2009-09-23
forum: Server Platforms
---

### Post by tribaldata on 2009-09-23
Hi everyone, 

I'm having a small issue but cannot seem to figure out where i could fix this.

I have a daily cron job running for logrotate and i keep getting this error and i would love to remove that entry for ntop. My problem is that i cannot find where logrotate grab this ntop. Anyone could help ?

This is my daily email for the cron job 

```
/etc/cron.daily/logrotate:
error: error accessing /var/log/ntop: No such file or directory
error: ntop:1 glob failed for /var/log/ntop/*.log
error: found error in /var/log/ntop/*.log , skipping
```

I tried ```
crontab -e
``` but there is nothing relevant to logrotate or ntop... I'm kinda confuse.

Thanks

---

### Post by 3L33T on 2009-09-23
> **tribaldata said:**
> 
This is my daily email for the cron job 

```
/etc/cron.daily/logrotate:
error: error accessing /var/log/ntop: No such file or directory
error: ntop:1 glob failed for /var/log/ntop/*.log
error: found error in /var/log/ntop/*.log , skipping
```


What version Ubuntu are you running?

This could be [BUG #277652]("http://bit.ly/F12CZ")

---

### Post by tribaldata on 2009-09-23
Distributor ID: Ubuntu
Description:    Ubuntu 9.04
Release:        9.04
Codename:       jaunty

I did check the bug concerning the logrotate i do not think this is related... but i could be mistaken
I will update the logrotate function in any case to the latest one.
I'm using logrotate version 3.7.7

I am just wondering where the logrotate find this ntop entry since it's been remove from the system for a long time.

/etc/logrotate.conf does not show anything funky...

---

### Post by tribaldata on 2009-09-23
FIXED

Ok, i should have know that... ](*,)

logrotate uses the folder /etc/logrotate.d/ as cue to what to rotate and i had an entry for ntop in there....

Once the ntop entry removed from the system i am able to run logrotate without receiving this error email in my root account.

Cheers :)

---

