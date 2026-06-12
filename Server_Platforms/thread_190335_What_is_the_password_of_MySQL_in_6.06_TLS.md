---
title: "What is the password of MySQL in 6.06 TLS?"
date: 2006-06-06
forum: Server Platforms
---

### Post by explorer1979 on 2006-06-06
Hi all,

I login by the general user account, and then enter "mysql"

It show me that "ERROR 1045 (28000): Access denied for user 'xxx'@'localhost' (using password: NO)

Do the 6.06 version's MySQL default have a password?? Or what is wrong on my step.

Thx for your time.

---

### Post by LordHunter317 on 2006-06-06
The MySQL root account does not have a password by default, like always.  But you didn't try to connect as root.

---

### Post by mjm115 on 2006-06-06
Try 'sudo mysql' and that should work for you.

---

### Post by explorer1979 on 2006-06-06
mjm115,

Yes, sudo mysql work for me now, thx

But new problems, how to give root a new password after login in

mysql>

enter what command to give root a password?

And do the defualt, the MySQL is full UTF-8 already or it is using latin1 for all charset?

Since I am Chinese, I need support multi-language, like big5, gb2312, Japanese, UTF8 at the same MySQL ...

---

### Post by LordHunter317 on 2006-06-06
That's not the right way to connect as MySQL root.

***MySQL users have NOTHING to do with system users.***

Connect as:```
mysql -u root database
```  If you want to change the password, you can use the mysqladmin command to do so.

As for locale, it comes with UTF-8 support, but it's probably not using it.  You'll want to edit /etc/mysql/my.cnf and set all the right charset options.  There are quite a few (they make it far more complicated than necessary) so be sure to read the documentation carefully.

---

### Post by adamkane on 2006-06-07
phpmyadmin is easier:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

---

