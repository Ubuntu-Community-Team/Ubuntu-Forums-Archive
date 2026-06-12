---
title: "High Availability services in Ubuntu"
date: 2011-08-26
forum: Server Platforms
---

### Post by aldav on 2011-08-26
Hello, I have the following configuration:
2 Ubuntu server nodes.
I have the same process installed on both servers
I want to be able to do the following. I want to create a sort of active-pasive configuration on both nodes. Node 1 running the process, but if the process falls I want Node 2 to start running the process. I don't want both nodes to be running the process at the same time, because the process is accessing a database and I don't want to configure a lock mechanism inside the database. Therefore, I need just one of the process be running at any time, but I need the process to be up all the time, it doesn't matter if it is running from Node 1 or Node 2.

How can I achieve this?

Thanks in advance

---

### Post by TravisZ on 2011-10-17
Hello aldav,

You should be able to accomplish this using something like [http://www.drbd.org]("http://www.drbd.org/") and [http://linux-ha.org/wiki/Heartbeat](http://linux-ha.org/wiki/Heartbeat).  DRBD is more or less networked raid1 but it can be configured in a active/passive mode.  It can failover applications such as MySQL as well as IPs between machines so if you have an application that is communicating over a private network connection (php connecting to MySQL over a 19.168.x.x IP) you can fail over a Virtual IP (VIP) between the to machines and as long as your applications code is directed towards that VIP it should continue functioning as expected.

If you have any questions about it please do let me know. :)

---

