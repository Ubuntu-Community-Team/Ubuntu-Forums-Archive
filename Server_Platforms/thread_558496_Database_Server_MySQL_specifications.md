---
title: "Database Server MySQL specifications"
date: 2007-09-24
forum: Server Platforms
---

### Post by s.s.swapnil on 2007-09-24
I just wanted to confirm that, whether MySQL shipped with server edition, offers complete database server solution or not ...

---

### Post by koenn on 2007-09-24
depends what you consider a "complete database solution" ...
MySQL is a 'comple relational database system' but in terms of triggers, stored procedures, transactions, locking,  etc I heard it has or used to have a somewhat  unusual implementation. MySQL was originally designed for use with web servers, and was therefore optimized for fast, easy read operations. I believe that's in the past now, but it wouldn't hurt to check. 

Also, if you expect loads of GUI management tools, drag-and-drop query creation tools etc as part of a 'complete' sollution, I don't think these are included by default. But is speaks SQL so any SQL frontend should be compatible.

---

### Post by az on 2007-09-24
Postgresql is in main.  I am not sure if it is on the cd or not.  Although, that's pretty irrelevant.

---

### Post by s.s.swapnil on 2007-09-25
Thanks koenn ....

'Complete Database Server' .... I'm very well aware of the fact that Stored Procedures, Materialzed Views n Triggers are not present in MySQL server.

My point of view about 'Complete Database Server / Solution' essentially means, a Dedicated Database Server who servers multiple concurrent users & multiple active databases for variety of different applications at the same time & can be easily administer remotely.

I'm pure microsoft guy & possess hands on experience in Microsoft SQL server & SQL Reporting Services since the earlier versions of MSSQL.

---

### Post by az on 2007-09-25
> **s.s.swapnil said:**
> Thanks koenn ....

'Complete Database Server' .... I'm very well aware of the fact that Stored Procedures, Materialzed Views n Triggers are not present in MySQL server.

My point of view about 'Complete Database Server / Solution' essentially means, a Dedicated Database Server who servers multiple concurrent users & multiple active databases for variety of different applications at the same time & can be easily administer remotely.

I'm pure microsoft guy & possess hands on experience in Microsoft SQL server & SQL Reporting Services since the earlier versions of MSSQL.

Then, yes, it's all there.

You would probably find it easier to administer using any one of the mysql frontends available to you.  You could set up mysql on am Ubuntu server and administer it remotely from a windows client using a GUI.

---

### Post by ukripper on 2007-09-25
MYSQL 5.0 includes stored procedures - [http://dev.mysql.com/tech-resources/articles/mysql-storedprocedures.html](http://dev.mysql.com/tech-resources/articles/mysql-storedprocedures.html)

---

### Post by s.s.swapnil on 2007-09-25
Well,

Now last question from my side ....

Is it ever possible to install n configure LAMP of ubuntu desktop configuration ? In other words, If i have LAMP standalone installer, can I install LAMP on ubuntu desktop operating system 6.0.6 ???

---

### Post by ukripper on 2007-09-25
[http://www.howtoforge.com/node/1388](http://www.howtoforge.com/node/1388)

---

### Post by oly on 2007-09-25
If you like your guis also install mysql-query-browser and mysql-admin they are both gui tools for mysql, available on windows and linux platforms.

---

### Post by Brazen on 2007-09-25
If you are setting up a web server anyway, you could also try phpMyAdmin for managing the MySQL server.  I've never used any of the other tools, such as MySQL Admin, but phpMyAdmin does everything I want and is super easy.

---

### Post by koenn on 2007-09-25
> **s.s.swapnil said:**
> 
Is it ever possible to install n configure LAMP of ubuntu desktop configuration ? In other words, If i have LAMP standalone installer, can I install LAMP on ubuntu desktop operating system 6.0.6 ???
I couldn't find a LAMP package, but if you run
```
sudo apt-get install apache php5 mysql-server

```
you're probably more than half way there. Throw in some of the sql front-ends or web admin tools suggested in this thread and you should be good to go. 
The link posted by ukripper does it the other way around : adding a desktop to a lamp server, but also includes some interesting tips for gui front-ends.

---

### Post by ukripper on 2007-09-26
You can install complete LAMP stack on existing Ubuntu Desktop using this guide -
[http://beans.seartipy.com/2006/11/14/installing-complete-lamp-stack-on-ubuntu-610edgy-eft/](http://beans.seartipy.com/2006/11/14/installing-complete-lamp-stack-on-ubuntu-610edgy-eft/)

---

### Post by az on 2007-09-28
> **s.s.swapnil said:**
> Well,

Now last question from my side ....

Is it ever possible to install n configure LAMP of ubuntu desktop configuration ? In other words, If i have LAMP standalone installer, can I install LAMP on ubuntu desktop operating system 6.0.6 ???

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Yes, you can install the LAMP stack on any Ubuntu machine.  It's not recommended on a production machine, since it goes against security best practices, but there is nothing per se about the packages that interfere with one another.

---

