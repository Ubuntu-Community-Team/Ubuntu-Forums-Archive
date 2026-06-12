---
title: "webmin 443 error error code -12263"
date: 2007-09-20
forum: Server Platforms
---

### Post by ratbastard on 2007-09-20
Hello all I set up webmin to listen on 443 but when I try to access I am getting error code -12263

I have no clue what this mean or how to go about fixing this error. 


I have the same set up on PC Linux OS and it works well. 


Any help would be most nice.. 

I am running LAMP 6.06 and all aspect of lamp are active and running if this helps.

---

### Post by tr333 on 2007-09-21
433 is the port for HTTPS.  You might need to pick a port number higher than 1024 (like 10000) to get this to work?  I'm not an expert on these things, so someone else might have a better idea.

---

