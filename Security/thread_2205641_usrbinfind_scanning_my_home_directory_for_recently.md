---
title: "/usr/bin/find scanning my home directory for recently modified files"
date: 2014-02-15
forum: Security
---

### Post by FreedomOverdose on 2014-02-15
Hello, 

After I noticed that my laptop's fan was loud even though nothing cpu-intensive was being run by me, I decided to see what process was causing using the CPU so much. To my surprise, I found the following process:
```
/usr/bin/find /home/<username> -mtime -60
```
being run by **root**, and taking 5+hours (not wallclock, i guess). 

First I thought that this might be backintime/zeitgeist doing a routine scan, however, the fact that it's running as root was suspictious to me. Unfortunately the process terminated before I could get its PPID and find more information about it. The process had a **niceness** of **10**.

Any ideas why process being run by root would scan my entire home directory for files modified in the last **60** days?

Thanks

---

### Post by Jonathan Precise on 2014-02-15
Post the outputs of:

```
sudo -i
crontab -e
```

Maybe (somehow) a crontab got installed by root to do that?

---

### Post by FreedomOverdose on 2014-02-15
> **Jonathan Precise said:**
> Post the outputs of:

```
sudo -i
crontab -e
```

Maybe (somehow) a crontab got installed by root to do that?

Already tried that; there's nothing in root's croontab :/

---

### Post by Dave_L on 2014-02-15
Does this help?
[http://ubuntuforums.org/showthread.php?t=2200904&p=12906812#post12906812](http://ubuntuforums.org/showthread.php?t=2200904&p=12906812#post12906812)

---

### Post by FreedomOverdose on 2014-02-15
> **Dave_L said:**
> Does this help?
[http://ubuntuforums.org/showthread.php?t=2200904&p=12906812#post12906812](http://ubuntuforums.org/showthread.php?t=2200904&p=12906812#post12906812)

Unfortunately the process stopped right before I could investigate a bit more, so currently it's not running...

---

### Post by FreedomOverdose on 2014-02-22
Found the job running again, traced its ppid this time. Turns out it is a tiger cron job (it didn't show in root's crontab, but it did show in the package specific crontab). 

So yeah, all looks good!

---

