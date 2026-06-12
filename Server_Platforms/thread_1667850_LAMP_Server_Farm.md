---
title: "LAMP Server Farm"
date: 2011-01-15
forum: Server Platforms
---

### Post by Raptor354 on 2011-01-15
Hello all!

I'm about to build a server farm that will load-balance, serve webpages, and run MySQL.  I've ran across a number of tutorials for programs such as keepalived and heartbeat, but they're all either for old(er) versions of Ubuntu (I'm running 10.10) or very incomplete (complete with poor English!).

I'd like to have a load balancer, an apache instance, and a MySQL server on a single node.  If there's a better way of handling that, I'd like to know about it.

At some point, I'll need to think about file replication across the nodes.

Does anybody have any thoughts, links, life experiences, or others' life experiences that might help in my quest?

Here's some interesting links to get things started.

[http://www.hbyconsultancy.com/]("http://www.hbyconsultancy.com/blog/two-nodes-load-balance-and-failover-with-keepalived-and-ubuntu-server-10-04-x64.html")

[http://www.howtoforge.com/]("http://www.howtoforge.com/set-up-a-loadbalanced-ha-apache-cluster-ubuntu8.04")

Thanks,

Raptor354

---

### Post by memilanuk on 2011-01-15
Dunno if this helps (it is for an older version of Ubuntu):

[https://help.ubuntu.com/community/HighlyAvailableLAMP](https://help.ubuntu.com/community/HighlyAvailableLAMP)

---

### Post by memilanuk on 2011-01-15
Dunno if this helps (it is for an older version of Ubuntu):

[https://help.ubuntu.com/community/HighlyAvailableLAMP](https://help.ubuntu.com/community/HighlyAvailableLAMP)

---

### Post by cariboo on 2011-01-15
Keepalived and heartbeat are in the Maverick repositories. The server installation and setup process hasn't changes for quite a while, any howtos you run into for 8.04 will work just fine for 10.10.

If you are going for high-availability, I would suggest you install 10.04, as it is supported for 5 years, whereas 10.10 is only supported for 2 years. You don't want to upgrade high-availability servers every two years.

---

### Post by hatemben on 2011-01-20
Hey Raptor, this is Hatem of HBYConsultancy. It's not really hard to implement HA cluster with ubuntu, however I don't know about your server farm size, the architecture you want to implement, number of servers, SAN storage, number of concurrent users, the ability to expand...

---

