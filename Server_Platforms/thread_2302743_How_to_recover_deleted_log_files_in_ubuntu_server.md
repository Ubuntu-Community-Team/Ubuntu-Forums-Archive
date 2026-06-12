---
title: "How to recover deleted log files in ubuntu server?"
date: 2015-11-12
forum: Server Platforms
---

### Post by chong_alburo on 2015-11-12
Hi,

I just deleted some log files to free up some disk space from the server (var/logs) and now when we reboot the server, the apache doesn't seem to start. Is it OK to delete log files? How to I recover them? or any solution you can recommend.

really need your help.
Thanks.

---

### Post by darkod on 2015-11-13
In theory you should be able to delete (some) log files. The only loss is the info within the files, because you can't look at it later if you need to.

Even with deleting log files apache should start. It should simply create new empty files and start filling them up.

For the future, most log files are included in what is called logrotate. On specific intervals the logrotate "removes" the actual log file, compresses it and keeps it like that for a specific number of iterations. It also creates new empty log file that starts to be used. You should be able to freely remove these older compressed log files, but not the actual file. Better to leave it in place.

If the log rotation is not as fast as you want it (the logs are getting big), you can change the setting. For example from monthly to weekly. That will empty the main log faster and create compressed archives. They will still fill up the disk over time, so you need to move the periodically to another location. That way you have freed space on the server, and you still have the logs in case you need them.

As for the current problem, have you tried creating new empty files instad of the ones you deleted and restart apache?

---

