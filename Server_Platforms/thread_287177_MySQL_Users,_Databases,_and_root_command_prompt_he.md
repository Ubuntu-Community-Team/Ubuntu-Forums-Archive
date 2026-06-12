---
title: "MySQL: Users, Databases, and root: command prompt help"
date: 2006-10-28
forum: Server Platforms
---

### Post by uncleclinto on 2006-10-28
First of all, I hope I'm in the right place.  The last time I was here, there was a forum called "server talk".  That seems to have been replaced by "servers and security".  My question has a whole lot to do with server and maybe not much with security.  Onward to glory:

I have a DapperDrake LAMP server running.  I installed MySQL Administrator because I was having so much trouble accessing MySQL at the command prompt.  It worked great for two weeks.  I was adding users and monitoring my databases like a pro.  Well, after my last update, MySQL admin locks up when I  so much as breathe on it, so we're back to the command line problem.

How do I get from the terminal prompt "~$" to the MySQL prompt "mysql>" ??  I looked in the documentation at [https://help.ubuntu.com/community/ApacheMySQLPHP#head-4961b97e928016223c108d998995476f17930c1c](https://help.ubuntu.com/community/ApacheMySQLPHP#head-4961b97e928016223c108d998995476f17930c1c)
and found nothing.  It says something about typing "mysql -u root" at the command prompt, but I get the message "Error 1045 (28000): access denied for user 'root'@'localhost' (using password: NO)", which is, incidentally, the same error I get if I type "mysql", "sudo mysql", or anything else having to do with mySQL.  Even when it asks for a password and I enter my root password, I get that same error message.  What am I missing??

---

### Post by uncleclinto on 2006-10-28
My question still stands about the command prompt, but I found a workaround for anyone running into the lock-up problem with the GUI administrator.  Type "DEBUG_DONT_SPAWN_FETCHES=1 mysql-admin" at the command prompt and MySQL Admin will open and work like a charm.  Yee Haw!!!

---

### Post by digeratess on 2006-10-29
For your command prompt problem, you have to type 

```
mysql -u root -p
```

The -p tells it to use a password.

---

### Post by digeratess on 2006-10-29
BTW, thanks for posting for workaround for mySqlAdmin. I didn't realize I had the same problem because I hadn't used the app in a few days, but I tried it out, and sure enough, it hangs everytime without prefixing the DEBUG... statement you posted.

---

### Post by Abhi Kalyan on 2006-11-04
> **digeratess said:**
> BTW, thanks for posting for workaround for mySqlAdmin. I didn't realize I had the same problem because I hadn't used the app in a few days, but I tried it out, and sure enough, it hangs everytime without prefixing the DEBUG... statement you posted.

Following on the foot steps mate!!!!

---

### Post by Yfrwlf on 2006-12-06
> **uncleclinto said:**
> My question still stands about the command prompt, but I found a workaround for anyone running into the lock-up problem with the GUI administrator.  Type "DEBUG_DONT_SPAWN_FETCHES=1 mysql-admin" at the command prompt and MySQL Admin will open and work like a charm.  Yee Haw!!!

Thanks a bunch for the work-around.  I'm sure someone has reported this bug several times to the devs already.  For me it would hang when I tried to select the User Administration area.  Otherwise, it seems like a good program :)

---

