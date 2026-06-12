---
title: "Logrotate: Error creating outfile, file already exists"
date: 2015-07-01
forum: Server Platforms
---

### Post by zemmiphobiahates on 2015-07-01
Hey, 

I've been running logrotate in a daily cron, yesterday I got an e-mail about a file already existing.
```
 error: error creating output file path/to/search.log.2014-10-03.1412289722.gz: File exists
```

Although, I'm not sure why I'm getting this error or how to fix it. The file that it's complaining about is only a few months old and the backlog allowance is 100 years. 

```
    /path/to/search.log {
      daily
      missingok
      rotate 36500
      compress
      delaycompress
      notifempty
      dateext
      dateformat .%Y-%m-%d.%s
      create 0644 user user
    }

```

I've checked file permissions on the directory and file, checked that it wasn't 0byte, I've removed the state file and tried running it manually. I'm kind of out of ideas :\ 

Running logrotate 3.8.7 on ubuntu 14.04

---

