---
title: "How to import table.sql to mysql?"
date: 2011-06-08
forum: Server Platforms
---

### Post by rado3105 on 2011-06-08
Hi I am trying to install some program: rosinfo:
 - Create mysql database for rosinfo
 - Create table hosts, locks. Use file docs/rosinfo.sql

And I need to create table hosts, locks, using file rosinfo.sql. I have that file, but dont know what to do with it.  Could you help?

---

### Post by sirhalos on 2011-06-08
First make sure you have mysql installed or whatever SQL server you will be using.

Second type 
mysql -u root -p

You should get a mysql prompt now from there type this

CREATE DATABASE rosinfo;

Don't forget the ;

Now exit mysql with this

EXIT;

Now you need to import the table type this in

mysql -u root -p -D rosinfo < rosinfo.sql

Lastly I would suggest getting phpmyadmin, it will make things much easier.

---

