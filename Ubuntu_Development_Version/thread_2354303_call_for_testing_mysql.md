---
title: "call for testing: mysql"
date: 2017-03-01
forum: Ubuntu Development Version
---

### Post by elopio on 2017-03-01
Hello!

Since January we have been making calls for testing to get more people involved in the quality of the new software that's making its way to the Ubuntu store. We need many hands. To participate you just need to have Ubuntu installed, we'll help you getting started with anything else that you need, or answering the doubts that you might have. This is a great way to start collaborating with free software because it doesn't require a lot of time, and it can serve you to take a look at some exciting projects that would love to get new contributors. Then you can jump to other types of collaboration, like packaging, bug fixing, automation, translations, documentation, or you can keep helping us testing the new projects that are constantly arriving.

MySQL is one of the projects that's pushing a new revision to the store. In order to test it, you'll just have to do:

```
$ sudo snap install mysql --channel=8.0/beta
```

Here's the testing guide to help you getting started:
[https://gist.github.com/elopio/c868bc68bf8640b0b49b39aeb1fae8f5](https://gist.github.com/elopio/c868bc68bf8640b0b49b39aeb1fae8f5)

This should run in trusty, xenial, yakkety, zesty and in all flavours of Ubuntu. It would be great to get a diverse pool of platforms and test it everywhere.

Please report back your results. Any kind of feedback will be highly appreciated, and if you have doubts or need a hand to get started, I'm hanging around in [https://rocket.ubuntu.com/channel/community](https://rocket.ubuntu.com/channel/community)

pura vida

---

### Post by cariboo on 2017-03-02
Just installed the snap and ran through all the test, mysql ran as it should.

---

### Post by #&amp;thj^% on 2017-03-02
> **cariboo said:**
> Just installed the snap and ran through all the test, mysql ran as it should.

+1 Same on my end also...mysql ran as it should.:KS
Edit: My tests were on "16.04.2" "With and Without yakkety HWE "... and "16.10" also.

---

### Post by ventrical on 2017-03-02
same here

```

 mysql.client -uroot -p
Using config file: /home/ventrical/snap/mysql/common/conf/my.cnf
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 4
Server version: 8.0.0-dmr

Copyright (c) 2000, 2016, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> help

For information about MySQL products and services, visit:
   http://www.mysql.com/
For developer information, including the MySQL Reference Manual, visit:
   http://dev.mysql.com/
To buy MySQL Enterprise support, training, or other products, visit:
   https://shop.mysql.com/

List of all MySQL commands:
Note that all text commands must be first on line and end with ';'
?         (\?) Synonym for `help'.
clear     (\c) Clear the current input statement.
connect   (\r) Reconnect to the server. Optional arguments are db and host.
delimiter (\d) Set statement delimiter.
edit      (\e) Edit command with $EDITOR.
ego       (\G) Send command to mysql server, display result vertically.
exit      (\q) Exit mysql. Same as quit.
go        (\g) Send command to mysql server.
help      (\h) Display this help.
nopager   (\n) Disable pager, print to stdout.
notee     (\t) Don't write into outfile.
pager     (\P) Set PAGER [to_pager]. Print the query results via PAGER.
print     (\p) Print current command.
prompt    (\R) Change your mysql prompt.
quit      (\q) Quit mysql.
rehash    (\#) Rebuild completion hash.
source    (\.) Execute an SQL script file. Takes a file name as an argument.
status    (\s) Get status information from the server.
system    (\!) Execute a system shell command.
tee       (\T) Set outfile [to_outfile]. Append everything into given outfile.
use       (\u) Use another database. Takes database name as argument.
charset   (\C) Switch to another charset. Might be needed for processing binlog with multi-byte charsets.
warnings  (\W) Show warnings after every statement.
nowarning (\w) Don't show warnings after every statement.
resetconnection(\x) Clean session context.

For server side help, type 'help contents'

mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY '********';
Query OK, 0 rows affected (0.00 sec)

mysql> SELECT VERSION(), CURRENT_DATE;
+-----------+--------------+
| VERSION() | CURRENT_DATE |
+-----------+--------------+
| 8.0.0-dmr | 2017-03-02   |
+-----------+--------------+
1 row in set (0.00 sec)

mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
4 rows in set (0.01 sec)

mysql> CREATE DATABASE menagerie;
Query OK, 1 row affected (0.00 sec)

mysql> USE menagerie
Database changed
mysql> CREATE TABLE pet (name VARCHAR(20), owner VARCHAR(20), species VARCHAR(20), sex CHAR(1), birth DATE, death DATE);
Query OK, 0 rows affected (0.04 sec)

mysql> SHOW TABLES;
+---------------------+
| Tables_in_menagerie |
+---------------------+
| pet                 |
+---------------------+
1 row in set (0.00 sec)

mysql> INSERT INTO pet VALUES ('Puffball','Diane','hamster','f','1999-03-30',NULL);
Query OK, 1 row affected (0.01 sec)

mysql> SELECT * FROM pet WHERE name = 'Puffball';
+----------+-------+---------+------+------------+-------+
| name     | owner | species | sex  | birth      | death |
+----------+-------+---------+------+------------+-------+
| Puffball | Diane | hamster | f    | 1999-03-30 | NULL  |
+----------+-------+---------+------+------------+-------+
1 row in set (0.00 sec)

mysql> QUIT
Bye
ventrical@ventrical-MS-7850:~$ 

```

---

### Post by howefield on 2017-03-02
> **elopio said:**
> This should run in trusty, xenial, yakkety, zesty and in all flavours of Ubuntu. It would be great to get a diverse pool of platforms and test it everywhere.

Tested on 16.04.2 with Yakkety HWE.. no issues, all works as expected.

---

### Post by elopio on 2017-03-02
Wow, that was a better response than what I expected. Thank you very much!
Now, you tell me that it works as expected. I would also be interested in knowing how you feel about the snap? Do you find it easier than going to the mysql website and installing it from a tarball. What about compared to a PPA? Any thoughts?

pura vida.

---

### Post by cariboo on 2017-03-02
> **elopio said:**
> Wow, that was a better response than what I expected. Thank you very much!
Now, you tell me that it works as expected. I would also be interested in knowing how you feel about the snap? Do you find it easier than going to the mysql website and installing it from a tarball. What about compared to a PPA? Any thoughts?

pura vida.

Why go to the website for a tarball when it's in the repositories. I usually only install mysql along with the rest of the lamp stack using tasksel during a server install.

---

### Post by elopio on 2017-03-03
well, the repositories have mysql 5.7. The one that you installed from the snap is mysql 8.0.
It will get to the repositories at some point. But there will still be users on trusty and xenial for a long time, and they are stuck with the old version in the repos.

---

### Post by cariboo on 2017-03-03
On an LTS versions, you don't want things to change much. On my 16.04.2 LTS server, it doesn't need the latest and greatest, as long as I get security updates it's happy.

I have several local web sites that rely on mysql, if I introduce a new version, who knows what is going to need updating.

---

### Post by howefield on 2017-03-03
> **elopio said:**
> Now, you tell me that it works as expected. I would also be interested in knowing how you feel about the snap? Do you find it easier than going to the mysql website and installing it from a tarball. What about compared to a PPA? Any thoughts?

The latest version in the repositories with very little chance of breakage, not sure why anyone wouldn't want that :)

PPAs can be horrible, the forum is littered with threads where a ppa has broken apt for one reason or another.

---

### Post by #&amp;thj^% on 2017-03-03
> **cariboo said:**
> On an LTS versions, you don't want things to change much. On my 16.04.2 LTS server, it doesn't need the latest and greatest, as long as I get security updates it's happy.

I have several local web sites that rely on mysql, if I introduce a new version, who knows what is going to need updating.
Very wise advice & +1...I also have a small testing partition with 16.04.2 to play with. 

> **howefield said:**
> 
_**PPAs can be horrible, the forum is littered with threads where a ppa has broken apt for one reason or another.**_
Yes indeed;) This is where the blood comes from in bleeding edge.:smile:
> **howefield said:**
> The latest version in the repositories with  very little chance of breakage, not sure why anyone wouldn't want that :smile:

+1 Just the proper thing to do.:smile:
Back on topic...nothing bad to report yet though on the snap mysql.

---

### Post by elopio on 2017-03-03
If you are happy with the version released in the archives of the distribution you are using, there is not much to gain by using a snap. That is true.

Now, on the ipfs case I mentioned on the other thread, the scenario is pretty different. It would be really hard to get ipfs in xenial, and almost impossible to get it in trusty. Not even zesty is easy at this point. And to get it into the z+1 release, we would have to get it into debian first which is more work than preparing the snapcraft.yaml and running snapcraft push. Finally, if we get the current version into the debian and ubuntu archives, it won't be very useful because IPFS is on the early stages of the 0.x release. It will become useful and stable at some point, but now what's important is to release often and get feedback from early adopters. The 6 month release cycle of ubuntu kills that.

It's great to hear your comments, please keep them coming. I'm not trying to convince you to switch from debs, if you are happy now, that's great. But if you are interested in snaps, there's plenty of things to do and we need more hands everywhere.

pura vida.

---

