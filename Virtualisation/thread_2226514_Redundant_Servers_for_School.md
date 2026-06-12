---
title: "Redundant Servers for School"
date: 2014-05-27
forum: Virtualisation
---

### Post by rick27 on 2014-05-27
Hello!

I am helping out a school and they want to get two servers that are setup to be redundant so that one acts as a backup in the event there is a failure on the main server. How is this possible with Ubuntu Server?

Thank you!
Rick

---

### Post by tgalati4 on 2014-05-27
Make sure you have a good UPS and you have the batteries on a change schedule.  Spend some time reading about high availability.

Define downtime.  How much downtime is acceptable?  Seconds, minutes, hours?  You could set up two identical servers and keep one asleep and use Wake-on-Lan if the heartbeat of one fails.  You could keep two servers running constantly and use some sort of checkpointing scheme to compare the running condition of both.  You could have two servers providing the same webpage and database and load-balancing between the two.   You could have one local server and one server in the cloud as a backup.

How you set it up depends on what your tolerance of downtime is.

Some reading:  [http://manpages.ubuntu.com/manpages/hardy/man8/wackamole.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/wackamole.8.html)

[https://help.ubuntu.com/community/HighlyAvailableLAMP](https://help.ubuntu.com/community/HighlyAvailableLAMP)

[http://manpages.ubuntu.com/manpages/hardy/man8/heartbeat.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/heartbeat.8.html)

---

### Post by TheFu on 2014-05-28
tgalati4 is correct.  Without the RPO, RTO and budget, it is impossible for us to recommend anything that will actually be useful. Look up those terms and have the client decide the numbers, knowing that 24hrs for RPO should be relatively easy (normal daily backups), but anything less will become more complex and more costly to install, configure, maintain (heavy on the maintain part for inexperienced Linux admins).

Oh - and the sort of workload will matter too.  Web servers can almost always be active-active with DNS or reverse proxies managing the failover, but DB servers are different. The kind of workload will lead to the best answer.  File servers will have a different solution - usually a file system clustering technique is best ... GlusterFS or something simlar - but the size of the files, amount of data changed and distance between the HA servers will matter greatly.

Also, be certain to invoke whatever solution gets installed weekly or monthly to ensure it works.  My systems fail-over to alternate servers every week - this is planned. It also makes the maintenance harder, but we all sleep better knowing that it works.  I've seen other systems setup for HA that were never really tested after the installation, pre-production use.  Then 2 yrs later when they needed the fail-over to work, it didn't.  That is worse, IMHO.

BTW - having HA servers in the same city is a bad idea.

---

### Post by rick27 on 2014-05-28
Thank you for your replies!!!

We are looking for failover to be transparent. Something like broadband balancing, when one internet connection drops, the other automatically carries the load.

Appreciate your feedback!

---

### Post by TheFu on 2014-05-28
Is this a network failover only?  If so - use pfSense and get 2 different network providers.

---

