---
title: "sql with php and mysql"
date: 2011-08-04
forum: Server Platforms
---

### Post by shubham1 on 2011-08-04
i want to setup sql(structured query langauge) with php and mysql is that library in ibuntu software center or terminal please tell in detail.my apache server is not restarting it gives error could not determine fully qualified server name.

---

### Post by Wim Sturkenboom on 2011-08-04
Your apache is starting fine (more than likely). The error is actually a warning; did you try to connect to [http://localhost](http://localhost) ? You should get a page 'It works'.

php and mysql (the server as well as the client) are in the repositories; I've never looked in the software center, but they should be in the repositories that you can access via the synaptic package manager (or apt-get in case of a command line).

PS
The apt-get way:
```

sudo apt-get install php5 mysql-server php5-mysql

```

---

### Post by shubham1 on 2011-08-05
i already have php mysql i want sql(structured query langauge) library for managing library

---

### Post by gouravgargg on 2011-08-05
is it domain name or server name in error

---

### Post by shubham1 on 2011-08-05
* Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
its domain name.

---

### Post by Wim Sturkenboom on 2011-08-05
> **shubham1 said:**
> i already have php mysql i want sql(structured query langauge) library for managing library
Sorry, but I'm not understanding.

**my** **S**tructured **Q**uery **L**anguage

The libraries should be installed; some of them even by default

```

wim@desktop-01:~$ sudo updatedb
wim@desktop-01:~$ locate mysql |grep so
/usr/lib/libmysqlclient.so.16
/usr/lib/libmysqlclient.so.16.0.0
/usr/lib/libmysqlclient_r.so.16
/usr/lib/libmysqlclient_r.so.16.0.0
/usr/lib/openoffice/basis3.2/program/libmysqllx.so
/usr/lib/qt4/plugins/sqldrivers/libqsqlmysql.so

```
This is before an install of the mysql server. So you're ready to develop software, if that is what you're looking for.

If you're looking for the client, it is installed as part of the server install. So you're ready to work on the databases straight away.

```

mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 41
Server version: 5.1.41-3ubuntu12.10 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
+--------------------+
2 rows in set (0.00 sec)

mysql> use mysql
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> select user,host,password from user;
+------------------+-----------+-------------------------------------------+
| user             | host      | password                                  |
+------------------+-----------+-------------------------------------------+
| root             | localhost | *7107096F9DC37F8F175584866ED48F080C3A3FE2 |
| root             | 127.0.0.1 | *7107096F9DC37F8F175584866ED48F080C3A3FE2 |
| debian-sys-maint | localhost | *A8180F94AA13F8A1B09E764359AACFA055712BBC |
+------------------+-----------+-------------------------------------------+
3 rows in set (0.00 sec)

mysql> 

```

If this is all not what you're after, I might have to explain a little better.

---

### Post by shubham1 on 2011-08-05
mysql is working but i am talking about sql
take look
[http://www.w3schools.com/sql/default.asp]("http://www.w3schoools.com/sql/default.asp")

---

### Post by manthony121 on 2011-08-05
What does Nascar Technical Institute have to do with SQL?

---

### Post by Wim Sturkenboom on 2011-08-05
Your link is wrong ! Should be [noparse]http://www.w3schools.com/sql/default.asp[/noparse], not [noparse]http://www.w3schoo[/noparse][COLOR="Red"]o[/COLOR][noparse]ls.com/sql/default.asp[/noparse]

You can follow that tutorial using mysql if that is what you want. I don't think that you will find one RMDBS that is 100% compliant with the SQL standard.

PS [this](http://dev.mysql.com/doc/refman/5.0/en/differences-from-ansi.html) is what MySQL states about the difference between MySQL and the standard (for MySQL V5.0.x)

---

### Post by shubham1 on 2011-08-06
waht is rmdbs

---

### Post by Wim Sturkenboom on 2011-08-06
Sorry, typo; should be rdbms

RDBMs; see [http://www.w3schools.com/sql/sql_intro.asp](http://www.w3schools.com/sql/sql_intro.asp)

---

### Post by shubham1 on 2011-08-07
i have seen this page many times.i want to install and setup.its a internal library.

---

### Post by shubham1 on 2011-08-07
that can be installed.

---

### Post by Wim Sturkenboom on 2011-08-07
Either I don't understand what you want (1) or you think that there is more to it than there acually is (2)

In case of:
1)
Please point to the exact page that refers to the library; I searched that page for the word *library* and could not find it
2)
See my post #6; just start the mysql client and start working; if you need help on creating databases, tables and some other basics, read e.g. [http://dev.mysql.com/doc/refman/5.0/en/tutorial.html](http://dev.mysql.com/doc/refman/5.0/en/tutorial.html)

Note:
Ubuntu does not seem to come with the 'test' database, so your results might slightly differ at some places to those in the above tutorial.

---

### Post by shubham1 on 2011-08-07
[http://www.w3schools.com/sql/sql_intro.asp](http://www.w3schools.com/sql/sql_intro.asp) page this contains many functions like mid avg join and many function that php
commands do not have.it is fast i also want the exact link to download
[http://www.sql.org/](http://www.sql.org/)

---

### Post by Wim Sturkenboom on 2011-08-07
The functions that you refer to on [http://www.w3schools.com/sql/sql_intro.asp](http://www.w3schools.com/sql/sql_intro.asp) are implemented in mysql. And that page does not contain the word *library* ;)

```

mysql> create table sometable ( i int, j int  );
Query OK, 0 rows affected (0.03 sec)

mysql> insert into sometable values(1,2);
Query OK, 1 row affected (0.00 sec)

mysql> insert into sometable values(3,4);
Query OK, 1 row affected (0.00 sec)

mysql> insert into sometable values(5,6);
Query OK, 1 row affected (0.00 sec)

mysql> select * from sometable;
+------+------+
| i    | j    |
+------+------+
|    1 |    2 |
|    3 |    4 |
|    5 |    6 |
+------+------+
3 rows in set (0.00 sec)

mysql> select avg(i) from sometable;
+--------+
| avg(i) |
+--------+
| 3.0000 |
+--------+
1 row in set (0.00 sec)

mysql> 

```

Your reference to PHP might start to make things a little clearer. I have the feeling that you want to use those functions directly in a PHP script or PHP based webpage. And that is not possible. The only way is
[LIST]
[*]connect to the mysql server using a php function
[*]select a database using a php function (assuming you have created a database)
[*]execute queries as shown above using a php function (assuming you have created tables)
[/LIST]
Those specific php functions are more than likely in php5-mysql, so that might be the library that you're referring to.

Quote from [http://www.w3schools.com/sql/sql_functions.asp](http://www.w3schools.com/sql/sql_functions.asp)
> 
SQL aggregate functions return a single value, [COLOR="Red"]calculated from values in a column[/COLOR].


---

### Post by shubham1 on 2011-08-07
ok let me test a few function then i will report that it works or not

---

### Post by shubham1 on 2011-08-07
yes it works
thanks for solving my problem.

---

### Post by shubham1 on 2011-08-07
now i can mark this thread as solved

---

### Post by Wim Sturkenboom on 2011-08-07
> **shubham1 said:**
> yes it works
thanks for solving my problem.Pleasure

---

