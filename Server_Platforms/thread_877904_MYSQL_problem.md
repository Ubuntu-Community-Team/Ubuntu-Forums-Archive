---
title: "MYSQL problem"
date: 2008-08-02
forum: Server Platforms
---

### Post by rado3105 on 2008-08-02
Hi I want to set password for mysql to install joomla and if I wrote > mysql -u root
it shows me this:

> r-c@ubuntu:~$ mysql
ERROR 1045 (28000): Access denied for user 'r-c'@'localhost' (using password: NO)

Can you help?

---

### Post by buntunub on 2008-08-02
I get the same thing. This happens on a pretty massive scale too. Try Google.

---

### Post by windependence on 2008-08-02
Try:

```
sudo mysql -u root 
```

-Tim

---

### Post by rado3105 on 2008-08-02
I also tried that: sudo mysql -u root the result same

I also tried google, nothing helped

---

### Post by windependence on 2008-08-02
Just FYI, there are TONS of responses to my google search. Let me check it out.

-Tim

---

### Post by windependence on 2008-08-02
If you have set a password you need to do:

```
mysql -uroot -p 
```


If not, try setting the password:

```
mysqladmin -u root password="yourpass" 

```

no password? try
```
mysql -uroot -p'' mysql
```

OR

```
mysql -uroot -ppassword mysql 
```

does the following give any errors?
```
>mysqladmin status
```

-Tim

---

### Post by StickyStyle on 2008-08-02
Sound's like you may have inadvertently set a root password for mysql, and not known what it is.

Take a look here for some techniques to reset your password [http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html#resetting-permissions-unix](http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html#resetting-permissions-unix)

I've usually gone with the ```
mysqld_safe --skip-grant-tables
``` method for when I help people out since it's quicker.

---

### Post by cariboo on 2008-08-03
When you install mysql on Ubuntu it asks you to set a password for root. You have to type it twice, use that one.

Jim

---

### Post by Wild-Storm on 2008-09-09
i've got the same problem. i tried several workarounds (dpkg-reconfigure, complete install and removal, different passwords, no passwords)
nothing works

logfile says:
		      5 Query       select @@version_comment limit 1
		      5 Query       SELECT count(*) FROM mysql.user WHERE user='root' and password=''

080909 18:12:43	      7 Connect     Access denied for user 'root'@'localhost' (using password: NO)

(i tried also using pwd: yes with my pw but same result.)


mysql> UPDATE mysql.user SET password='' WHERE user='root';

even after that there's still a hash...


edit://

whatever pass i enter in this skiptable thing, the hash always remains the same!

mysql> UPDATE mysql.user SET password=PASSWORD('1234') WHERE user='root';
Query OK, 0 rows affected (0.00 sec)
Rows matched: 0  Changed: 0  Warnings: 0


mysql> UPDATE mysql.user SET password='' WHERE user='root';
Query OK, 0 rows affected (0.00 sec)
Rows matched: 0  Changed: 0  Warnings: 0

even that doesnt help...

edit:// omfg, there is no root user -.- what the heck...
got it working now by creating user root...

---

