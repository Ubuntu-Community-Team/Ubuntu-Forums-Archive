---
title: "after upgrade mysql to 5.5, server won't start"
date: 2013-08-09
forum: Server Platforms
---

### Post by andrejmoky on 2013-08-09
Hello,

after I upgrade my mysql server to mysql-server 5.5.32-0ubuntu0.12.04.1 my server dont start.I have changed default data dir to /home/mysql. Rights are corects. When I change data dir to default - /var/lib/mysql, server works. 

What should I do, to change data dir to /home/mysql?

Thank you.

---

### Post by lykwydchykyn on 2013-08-09
Have you checked the log files for errors?

My guess is that you're running afoul an apparmor policy that prevents the mysql server process from reading or writing to /home/.

---

### Post by Cheesemill on 2013-08-10
*Thread moved to **Server Platforms**.*

As this is a support request I've moved it here, you should get more of the right people seeing this thread.

+1 for it being an apparmour problem. Did you edit the MySQL apparmour configuration to allow it to access your home folder?

---

### Post by andrejmoky on 2013-08-11
Thank you for help.

I added 
/home/mysql r,
/home/mysql/** rwk

to etc/apparmor.d/usr.sbin.mysqld

restart apparmor and mysql and everything works.

---

