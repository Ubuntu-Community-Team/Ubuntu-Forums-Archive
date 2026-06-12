---
title: "Network monitoring"
date: 2010-11-16
forum: Server Platforms
---

### Post by blozancic on 2010-11-16
Hello all; I'm looking for something that will help me do some monitoring of servers, switches and ip cameras over the internet.  
Two of the apps I've looked at are Nagios and Splunk.  
What we need is a distributed environment.  Each group of cameras has a an Ubuntu server.  Some of the servers are behind closed firewalls.  
Can Nagios, or something like it, have a central server that receives, not pulls, info from all these distributed servers and then reports status on the other servers and their network equipment?

---

### Post by arrrghhh on 2010-11-16
Nagios and Zenoss would by my recommendations.

---

### Post by tonyyarusso on 2010-11-18
Yes, Nagios can be configured that way.  Look for the documentation on "passive checks" and NSCA.

---

