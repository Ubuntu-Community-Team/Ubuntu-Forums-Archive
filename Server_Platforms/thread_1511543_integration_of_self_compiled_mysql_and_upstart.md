---
title: "integration of self compiled mysql and upstart"
date: 2010-06-16
forum: Server Platforms
---

### Post by yongjie on 2010-06-16
Hi,

I have a 10.04 server,and official mysql server installed. But I decided to compile the mysql server myself, and installed it under /usr/local/mysql.

Now, after reboot, the server will automatically restart the official mysql server under /usr.

I want to change the init.d/mysql scripts using the mysql.server provided by the mysql source tree. 

But the mysql init.d script is already migrated to use the upstart mechanism which I am not familar with. How could change the configuration file(s) so the auto start process will start my self compiled mysql server under /usr/local/mysql.

Thanks for the help

---

