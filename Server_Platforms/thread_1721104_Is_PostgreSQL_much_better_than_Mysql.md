---
title: "Is PostgreSQL much better than Mysql?"
date: 2011-04-04
forum: Server Platforms
---

### Post by 007casper on 2011-04-04
Is PostgreSQL much better than Mysql?

what are the pros/cons?

---

### Post by 007casper on 2011-04-06
I am really trying to figure out the cons and pros of both.  Some believe PostgreSQL to be fast compare to Mysql.  Which one is better for heavy production environment?

thank you.

---

### Post by sahabcse on 2011-04-06
MySQL has long been assumed to be the faster but featureless of the two database systems, while PostgreSQL was assumed to be a more densely featured database system often described as an open-source version of Oracle.

---

### Post by julianb on 2011-04-06
[Wikivs on Postgresql versus mysql]("http://www.wikivs.com/wiki/MySQL_vs_PostgreSQL")

---

### Post by SeijiSensei on 2011-04-06
That is a very informative article!  Thanks.

I'm still sticking with PostgreSQL.  I never understood quite why MySQL is seen as easy to use, though.  I find it a pain for common admin tasks like adding new users and new DBs.  In PG, there are simple command-line programs like "createuser" and "createdb"for these tasks. In MySQL you have to accomplish these tasks by running INSERTs with the mysql client. I also prefer managing access controls in the pg_hba.conf file rather than the 'user'@'location' method in MySQL.

I've used PG for over a decade as the back-end to web applications.  It never feels "slow" at those tasks, though I'm not supporting large numbers of concurrent transactions.

---

### Post by sahabcse on 2011-04-07
Some more info about postgre and mysql related to webhosting 

[MySQL vs. PostgreSQL]("http://forums.ubuntulinux.co.in/index.php/topic,588.0.html")

---

### Post by garfonzo on 2011-04-07
> **SeijiSensei said:**
> That is a very informative article!  Thanks.

I'm still sticking with PostgreSQL.  I never understood quite why MySQL is seen as easy to use, though.  I find it a pain for common admin tasks like adding new users and new DBs.  In PG, there are simple command-line programs like "createuser" and "createdb"for these tasks. In MySQL you have to accomplish these tasks by running INSERTs with the mysql client. I also prefer managing access controls in the pg_hba.conf file rather than the 'user'@'location' method in MySQL.

I've used PG for over a decade as the back-end to web applications.  It never feels "slow" at those tasks, though I'm not supporting large numbers of concurrent transactions.

I'm just starting to build web apps and am using MySQL, for no specific reason. I too find it ridiculous how one goes about creating a new user or a new database in MySQL. I'm thinking of switching to PG though based on some of the info in that article linked above, and fortunately with django it would be an easy switch I think.

---

### Post by 007casper on 2011-04-10
those links are great.  It is quite extensive.

Looking around has anyone used H2

[http://www.h2database.com/html/performance.html](http://www.h2database.com/html/performance.html)

it is claiming second to none in performance

---

### Post by 007casper on 2011-04-14
has anyone tried H2 as a database?

---

### Post by Vegan on 2011-04-14
I stick to the standard LAMP stack as its well trodden and well documented.

Either database is fine, but MySQL has been the popular LAMP choice simply due to the tight integration with PHP making it super easy to use.

---

### Post by SeijiSensei on 2011-04-15
MySQL is no more "tightly" integrated with PHP than PostgreSQL.  PHP has an extensive array of functions to communicate with both databases (and [many others]("http://www.php.net/manual/en/refs.database.php") as well).  

The prevalence of LAMP had more to do with MySQL's claimed performance benefits back in the day, and, I suspect, because it has an easily-remembered acronym.  LAPP never seemed to catch on.

---

### Post by lykwydchykyn on 2011-04-15
I switched my development to postgres a few years ago and never looked back.  The features are better, and IMHO the SQL syntax is just cleaner.  Embedded functions are addictive, too.

The only reason I still work with MySQL from time to time is that you can't really count on anything else being available from your client's cheap web host.

---

