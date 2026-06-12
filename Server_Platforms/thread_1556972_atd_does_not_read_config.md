---
title: "atd does not read config"
date: 2010-08-20
forum: Server Platforms
---

### Post by mneisen on 2010-08-20
Hi,

I run a server on 9.10 and have noticed that atd is now started using upstart. 

Problem is, that the config in /etc/default/atd does not seem to be included so atd runs with the standard parameters (only start batch jobs when load is < 1.5; start batch jobs 60 secs apart) which are not quite satisfying on a big SMP machine. 

Is there any way to get the upstart-script to read the config in /etc/default/atd? Is there any other way to configure atd when using upstart ? 

Thanks in advance!

---

