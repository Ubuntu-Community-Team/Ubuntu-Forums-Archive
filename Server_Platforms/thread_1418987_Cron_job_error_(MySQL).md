---
title: "Cron job error (MySQL)"
date: 2010-03-01
forum: Server Platforms
---

### Post by dwp0980 on 2010-03-01
Hello,

I'm hoping someone can point me in the right direction regarding a cron error mesage that I have received (via email).  I'm not sure where to start to try and find out what has gone wrong and why.  Below is the error text received from cron.  Any help gratefully received.

```
/etc/cron.daily/logrotate:
error: error running shared postrotate script for '/var/log/mysql.log
/var/log/mysql/mysql.log /var/log/mysql/mysql-slow.log '
run-parts: /etc/cron.daily/logrotate exited with return code 1
```

---

### Post by kiranmurari on 2010-03-02
Hi,
   
The following link might be helpful.
 [http://www.lornajane.net/posts/2008/Logrotate-Error-on-Ubuntu](http://www.lornajane.net/posts/2008/Logrotate-Error-on-Ubuntu)

---

### Post by dwp0980 on 2010-03-03
Yes, that did the trick.  I thought I had already sorted this, but I had got a zero and a capital O confused! Doh!

Thanks for the help.

---

