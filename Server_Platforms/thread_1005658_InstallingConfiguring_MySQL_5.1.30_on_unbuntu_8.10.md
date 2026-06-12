---
title: "Installing/Configuring MySQL 5.1.30 on unbuntu 8.10"
date: 2008-12-08
forum: Server Platforms
---

### Post by ShaolinF on 2008-12-08
Hi Guys

I am trying to install mysql from source on my distro. I am using the following tutorial to install it:
[http://dev.mysql.com/doc/refman/5.1/en/quick-install.html](http://dev.mysql.com/doc/refman/5.1/en/quick-install.html)

The problem is when I get upto the following line in the tutorial:
**bin/mysql_install_db --user=mysql**

I get the following error:

```
Moe@Moe-desktop:/usr/local/mysql$ bin/mysql_install_db --user=mysql
Installing MySQL system tables...
081208 19:25:11 [ERROR] /usr/local/mysql/libexec/mysqld: unknown option '--skip-federated'
081208 19:25:11 [ERROR] Aborting

081208 19:25:11 [Note] /usr/local/mysql/libexec/mysqld: Shutdown complete


Installation of system tables failed!  Examine the logs in
/usr/local/mysql/data for more information.

You can try to start the mysqld daemon with:

    shell> /usr/local/mysql/libexec/mysqld --skip-grant &

and use the command line tool /usr/local/mysql/bin/mysql
to connect to the mysql database and look at the grant tables:

    shell> /usr/local/mysql/bin/mysql -u root mysql
    mysql> show tables

Try 'mysqld --help' if you have problems with paths.  Using --log
gives you a log in /usr/local/mysql/data that may be helpful.

The latest information about MySQL is available on the web at
http://www.mysql.com/.  Please consult the MySQL manual section
'Problems running mysql_install_db', and the manual section that
describes problems on your OS.  Another information source are the
MySQL email archives available at http://lists.mysql.com/.

Please check all of the above before mailing us!  And remember, if
you do mail us, you MUST use the /usr/local/mysql/bin/mysqlbug script!
```
Does anyone know what I am doing wrong ?


.
.
.
.
.
.

---

### Post by lykwydchykyn on 2008-12-09
Never tried this, but see if it works.  Locate your my.cnf file, and search for the line that says "skip-federated".  Comment out that line by placing a # at the beginning.

---

### Post by wcorey on 2008-12-11
I, too, had difficulty getting the 5.1.30 GA version of MySQL installed. I am not convinced it is correct and The client apps that go with it do not get pushed to the Application/Programing menu. Further, as Sun/MySQL fix all those fatal bugs we heard of updates are not forthcoming. Consequently does anyone know?

1) When will there be a Ubuntu 5.1.x package?
2) Is creating the package a Sun/MySQL issue or a Ubuntu issue?
3) Who should be pestered to produce such a package if it is not already in the works?

Thanks,

Walt

---

### Post by PeterK2003 on 2009-03-31
i also would like a 5.1 install!

---

### Post by cariboo on 2009-03-31
Mysql-server-5.1 is in the Jaunty repositories.

Jim

---

### Post by PeterK2003 on 2009-03-31
oh really???  I will need to check that out...thanks!

---

