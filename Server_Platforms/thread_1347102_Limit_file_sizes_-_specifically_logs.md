---
title: "Limit file sizes - specifically logs?"
date: 2009-12-05
forum: Server Platforms
---

### Post by guessswh0 on 2009-12-05
Hi there,

I'm a little new, and I'm managing a linux vps.  Log file sizes are one thing I am wanting to limit.  logs for everything basically, mysql, apache, user logins to the server, everything.  How do I limit the sizes of files, specifically the logs?

Thanks for any help

---

### Post by brettg on 2009-12-05
Is there a reason that the way the logging works by default is unacceptable? What are you trying to achieve or mitigate?

Anyhoo, logs are (should be) already size limited. You can use the [logrotate]("http://linuxcommand.org/man_pages/logrotate8.html") daemon to configure how often they roll over etc

See [here]("http://www.linuxconfig.org/Logrotate") for examples and stuff

---

### Post by BkkBonanza on 2009-12-06
If you want to prevent the logs from growing too big then log rotation may make the most sense combined with a cron backup script to archive elsewhere perhaps. 

One way you could limit size of any specific subtree in your filesystem eg. /var/log would be to create a loop filesystem and mount it at the relevant location.

You create a file that contains a filesystem using loop and mount it at /var/log. Since the file is of a pre-determined size it cannot grow bigger.

This page gives a step-by-step but you would mount at /var/log/ not /mnt/vfs

[http://www.walkernews.net/2007/07/01/create-linux-loopback-file-system-on-disk-file/](http://www.walkernews.net/2007/07/01/create-linux-loopback-file-system-on-disk-file/)

This method would still give you trouble when it is full but would make sure your logs don't prevent other space problems that may end up in denial of service. There are ways to do log rotation based on size rather than time that may be what you need if you're worried about a DOS attack related to log size.

---

