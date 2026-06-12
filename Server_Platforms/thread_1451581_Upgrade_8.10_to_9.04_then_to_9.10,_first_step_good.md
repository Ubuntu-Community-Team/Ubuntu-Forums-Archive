---
title: "Upgrade 8.10 to 9.04 then to 9.10, first step good..."
date: 2010-04-10
forum: Server Platforms
---

### Post by kpm on 2010-04-10
not so much...
After the upgrade from 8.10 to 9.04, all was well.  But after the upgrade from 9.04 to 9.10, I lost the MySQL server.
Now, I recall during the upgrade, I was asked if I wanted to keep the existing my.cnf file or replace it with a newer one.  I did as suggested and kept the original as I had edited it before.  The same question was asked with a couple other config files.  I kept the original in each case.
After the first step, I checked the server was running and the websites were up, all was well.  After the update to 9.10, when I checked the server, I get the following error:

```
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)' 
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
```

Can anyone point me in the right direction to getting this resolved?
Thanks

---

### Post by s_ø on 2010-04-10
What command do you use when you get that error?
You can use the following command to get all mysql entries in the syslog
[B]grep -i 'mysql' /var/log/syslog
[/B]
Check that **/var/run/mysqld/mysqld.sock **exists. You can use the ls command
**ls -l /var/run/mysqld/mysqld.sock **

check the status of your mysql server
**sudo service mysql status**

---

### Post by kpm on 2010-04-10
Thanks for the input.

I found the answer here [http://ubuntuforums.org/showthread.php?p=9104694#post9104694](http://ubuntuforums.org/showthread.php?p=9104694#post9104694)

I had to comment out skip-bdb from my.cnf.

---

