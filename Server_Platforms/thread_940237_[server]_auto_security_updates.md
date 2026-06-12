---
title: "[server] auto security updates"
date: 2008-10-06
forum: Server Platforms
---

### Post by analoog on 2008-10-06
Are security updates installed automatically? Is there maybe a script/configuration option to do this?
Or is it recommended that I use apt-get regularly.

---

### Post by pdwerryhouse on 2008-10-06
They aren't fetched automatically. You could do this with cron:

```
0 3 * * * apt-get update && apt-get -y upgrade
```

I wouldn't really recommend it, though, as you never know what might break...

---

### Post by lykwydchykyn on 2008-10-06
It seems that the practice is generally discouraged, but it can be done.  There is a package called cron-apt that you can install which sets up cron jobs to automatically apt-get update and download the updates.   You can further configure it to attempt to install them and email you the results.  I've set it up on several (non-mission-critical) servers, and it seems to work well.

I don't have access to the config files I changed at the moment, but if you do some searching on cron-apt dist-upgrade you're likely to find what you need to do.

---

### Post by analoog on 2008-10-07
Thanks!

---

