---
title: "pm2 Startup not working on ubuntu 15.10"
date: 2016-01-15
forum: Server Platforms
---

### Post by Mendy_Danzinger on 2016-01-15
Since updating to 15.10, I am having issues gettings pm2 to restart (itself, and a node file) on a server re-boot.  

Below are the processes I have tried to no avail;

```
pm2 startup
pm2 start app.js
pm2 startup ubuntu 
pm2 save
```

My dump.pm2 file contains no information, so I am not sure where else to look.


I attempted to modify my ```
/etc/init.d/pm2-init.sh
``` file in accordance with [this issue]("https://github.com/Unitech/PM2/issues/1321"), but it did not help. 

Do I need to modify any additional files to get this working?



Thank you for your help in advance,

Mendy Danzinger

---

