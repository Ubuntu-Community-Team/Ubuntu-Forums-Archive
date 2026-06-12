---
title: "Testing Heartbeat"
date: 2007-09-16
forum: Server Platforms
---

### Post by reloded on 2007-09-16
Hi.

I have a few questions about Heartbeat. I've installed it on two nodes and the services started okay. I have set it up to monitor Apache2. Now, apart from successfully starting, is there a way to test that it will actually kick in when the main server goes down?
In my own very crude logic, I thought I'd test it by creating a basic html page with the name of each server. I then stop apache on the main server. When I try to access the main server via [http://serverip/index.html](http://serverip/index.html), it is not accessible. Even after the stipulated time that heartbeat should bring on the second node.
I was expecting to still run  [http://serverip/index.html](http://serverip/index.html) and with heartbeat detecting that it is down, it will direct me to the second node. 
Maybe I haven't still gotten the concept of heartbeat. how is it supposed to work. :confused:

Please assist.

Then, in my setup process, I got this error when running the command:  **/etc/init.d/heartbeat start**:
> heartbeat: 2007/09/16_07:14:20 ERROR: Illegal directive [use_logd] in /etc/ha.d/ha.cf
I then went to ha.cf and disabled use_logd. And from there the service started fine. Why is this? What exactly is logd?

Finally: Am running:
Ubuntu Fiesty Fawn
Heartbeat version 1.2.5
Installed it via apt-get install heartbeat
I have 2 nodes in my cluster running apache

---

### Post by Spark19 on 2008-07-23
Reloded,

Did you get this figured out?

Thanks!

---

