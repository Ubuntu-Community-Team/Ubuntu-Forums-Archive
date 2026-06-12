---
title: "freeRadius Authentication"
date: 2014-04-17
forum: Server Platforms
---

### Post by thomas.l.hull on 2014-04-17
I just recently built a basic free radius server to use as Authentication on our network. 
I have it setup so when a user logs into a switch they log in with read only privileges , and have to enter the ENABLE credentials. 

However, I do not want this on all of my devices, on my switches and routers yes, but with the APC UPS I would like them to Automatically login as Admin. Is there anyway I can do this?

Lastly, is there a way I can use freeRadius to log when users access any of the switches and routers?

Thanks in advanced for your time.

---

### Post by thomas.l.hull on 2014-04-17
Please disregard, we found the solution.

under /etc/freeradius/users 
 you need to edit Service-Type to look like the following.

Service-Type = NAS-Prompt-User,APC-Service-Type = admin,

---

