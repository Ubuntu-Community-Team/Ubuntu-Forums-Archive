---
title: "MySQL access"
date: 2011-04-15
forum: Server Platforms
---

### Post by BigYellowDog on 2011-04-15
I can not access my MySQL database from any remote host on my home network, I keep getting "Access denied for user 'dbuser'@'192.168.1.10' (using password: YES)"

From what I've read this seems to be a permission problem, I tried 

'dbuser'@localhost';
'dbuser'@'%';
'dbuser'@'192.168.1.10';

and between each change of permission, I've  flushed privileges.  Any help would be greatly appreciated.

---

### Post by usatonycuba on 2011-04-15
> **BigYellowDog said:**
> I can not access my MySQL database from any remote host on my home network, I keep getting "Access denied for user 'dbuser'@'192.168.1.10' (using password: YES)"

From what I've read this seems to be a permission problem, I tried 

'dbuser'@localhost';
'dbuser'@'%';
'dbuser'@'192.168.1.10';

and between each change of permission, I've  flushed privileges.  Any help would be greatly appreciated.
This might help you.. >> MySQL [Causes of Access-Denied Errors]("http://dev.mysql.com/doc/refman/5.1/en/access-denied.html")

---

