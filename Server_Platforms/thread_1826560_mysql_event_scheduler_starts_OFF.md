---
title: "mysql event_scheduler starts OFF"
date: 2011-08-16
forum: Server Platforms
---

### Post by melvinlopez06 on 2011-08-16
Hello!
Long time ago to not log in on this forum.

Please help!
I have a ubuntu server (9.10, karmic), running mysql (version: 5.1.37-1ubuntu5.1).

I have 1 data base using events for one intranet system, fine!
I edited the config file (/etc/mysql/my.cnf), and add this line:

event_scheduler=on

After, reboot mysql service, and query SHOW VARIABLES, and event_scheduler still OFF.

I rebooted the server, and again, event_scheduler still off.

the only way to change the value is executing this query:
SET GLOBAL event_scheduler=on; as root.

apparently is not taking the value saved on my.cnf

In fact, I Looked at syslog, and mysql successfully loaded all events of the database.

any idea?
suggestions?

thank you!

---

