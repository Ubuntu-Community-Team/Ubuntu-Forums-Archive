---
title: "lower apache2 and mysql memory usage"
date: 2007-02-18
forum: Server Platforms
---

### Post by istrebitjel on 2007-02-18
Good day,

I use my rather old Thinkpad (300MHz Celeron) with only 186MB ram to run mainly as an nfs server and also to run [Jinzora]("http://www.jinzora.org"), which requires apache and mysql.

The system is sometimes quite sluggish and I noticed both apache2 and mysql run a lot of child processes and seem to consume most of my memory. I'm pretty much the only one using them, so I wonder, how can I configure those to be a little more frugal with memory? 

This section in apache2.conf looks promising: Server-Pool Size Regulation (MPM specific)
But what are the right values for my setting? Will reducing StartServers to 1 influence my performance negatively? And which of the IfModule sections is the relevant one?

I didn't see anything I understood in my.cnf for mysql.

I tried some googling on the topic, but everything is targeted at more performance, nobody wants to conserve memory ;)

Thanks for any pointers!

---

### Post by James79 on 2007-02-24
Hi... since no one has replied to you I'll take a stab at it.

I'm running a similarly spec'd server... Thinkpad laptop, celeron 550mhz with 128mb. This server runs LAMP, OpenSSH and NFS.

Programs like Apache don't usually come with provisions for limiting their resource consumption, as typically you want such services to run as quickly as possible. Even bandwitdth throttling was difficult to setup.

But I don't think any of that really matters to you... I don't think your problem is ram, it's simply that your CPU is perhaps a little too weak to handle what you want to do. Unforuntely as you have an old laptop, it's probably not possible to upgrade it. I have the same problem. :-| 

Hope that helps!

---

### Post by istrebitjel on 2007-02-26
Thanks for your reply, James79!
For sure, upgrading RAM and CPU would be ideal, but not feasible. And I'm actually reasonably happy with the server performance, just working on the system is sluggish.

In the mean time I did some experimentation and found disabling InnoDB to be a huge memory safer for mysql:
(from /etc/mysql/my.cnf )
> # InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
# You might want to disable InnoDB to shrink the mysqld process by circa 100MB.
skip-innodb

I don't really know, what I'm doing, but it uses considerably less memory (from 100M+ Virt  per process to 20K) and I didn't notice a performance loss.

Thanks again for taking the time to reply!

---

