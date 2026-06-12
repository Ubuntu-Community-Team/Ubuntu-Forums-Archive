---
title: "mysql config on EC2"
date: 2010-06-24
forum: Server Platforms
---

### Post by kpgalligan on 2010-06-24
Holy crap pants.  Sometimes I really don't like the linux/mysql deal.

I have an ubuntu EC2 instance.  Mysql would start fine stock.  However, I copied the data dir to an EBS block.  I chown'ed the dir recursively to mysql:mysql.  I changed my.cnf to point to it.  I added the data dir in the apparmor config.

After that, if I try to start with:

/etc/init.d/mysql start

It will spit out a warning about using 'service mysql start'.  However, you'd think it would start anyway.  No start.  Worse, no message in /var/log/syslog

I try with 'service mysql start'.  The command line just locks.  Never returns.  Nothing in logs.

I made sure the drive was mounted properly.  It didn't auto mount after a restart.  I also restarted apparmor, just to make sure.

No luck.  While I'd expect problems, the really frustrating thing is no logging.  Any ideas?  I was under the impression that ubuntu-mysql was set up to log to syslog rather than a dedicated mysql log.  True?  No?  I'll dig into the my.cnf to get more info.

Thanks in advance.

---

### Post by kpgalligan on 2010-06-24
So weird.  I essentially jiggled the handle for an hour and got it to work.  Not sure what was really different.

I started mysqld manually.  Got that to work.  Then started with init.d, and it started fine.

---

