---
title: "MySQL pwd file"
date: 2011-05-16
forum: Security
---

### Post by Dronga on 2011-05-16
Hi All

Where is the mysql 5 password's file?

Thanks!

---

### Post by CharlesA on 2011-05-16
Are you trying to reset a password, or move an existing database to a new install of MySQL?

---

### Post by Dronga on 2011-05-16
No. 
I can reset password in console or phpmyadmin. But i want to find a physicaly file with password's...

---

### Post by CharlesA on 2011-05-16
I thought they were stored in the database. A quick [google]("http://www.google.com/#sclient=psy&hl=en&source=hp&q=where+are+mysql+passwords+stored&aq=0&aqi=g1&aql=f&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=668845393480168f") showed conflicting information.

---

### Post by tgm4883 on 2011-05-17
IIRC they are stored in the db, although you can reset the root password if necessary. Why are you trying to access mysql user passwords?

---

### Post by Dronga on 2011-05-17
Somethink find:
[http://dev.mysql.com/doc/refman/5.1/en/instance-manager-security-passwords.html](http://dev.mysql.com/doc/refman/5.1/en/instance-manager-security-passwords.html)

Sometimes passwords stored in /etc/mysqlmanager.passwd

> Why are you trying to access mysql user passwords?
Just intresting...

---

