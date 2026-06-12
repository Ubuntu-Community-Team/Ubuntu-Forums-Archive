---
title: "How would you debug this - sluggish performance, programs not starting ..."
date: 2008-04-18
forum: Server Platforms
---

### Post by cwmoser on 2008-04-18
How would you go about analyzing a case of sluggish performance and programs not starting?  I remote into my Ubuntu PC using NXServer from work.  When I return home and log into my Ubuntu PC, sometimes, not always, performance is sluggish and sometimes when I click on an Icon to run an application, they just will not start.  Once I reboot my Ubuntu PC, all is well.

So, how would you suggest one analyze why this happens?  All I know how to do is look at the /var/log/messages file but sometimes that is quite cryptic if you are as inexperienced as I am.

Any suggestions and comments are welcome.

Thanks

Carl

---

### Post by AlphaWu on 2008-04-18
This is my suggestions.
1.sudo apt-get autoremove
2.sudo apt-get clean

3.System--Administration--Services-----Unchecked the service you DON'T want start

---

