---
title: "MSSQL alternative problem"
date: 2008-06-16
forum: Server Platforms
---

### Post by anystupidname on 2008-06-16
I have a dilemma. We have an internal app that is written to use an M$SQL server only. I would like to use ANY sql server other that MSSQL. I'm hoping there is a mysql "connector" or some other way to do this. I cannot run MSSQL in WINE or  on a winblows box...

Any suggestions would be much appreciated!

---

### Post by cpetercarter on 2008-06-16
I don't know of an application which will do this. When writing a database application, it is often sensible to make it independent of a particular db package eg by using adodb ([http://adodb.sourceforge.net](http://adodb.sourceforge.net)) so that it can be migrated easily.

---

### Post by windependence on 2008-06-16
[http://www.kofler.cc/mysql/mssql2mysql.html](http://www.kofler.cc/mysql/mssql2mysql.html)

-Tim

---

### Post by anystupidname on 2008-06-20
> **cpetercarter said:**
> I don't know of an application which will do this. When writing a database application, it is often sensible to make it independent of a particular db package eg by using adodb ([http://adodb.sourceforge.net](http://adodb.sourceforge.net)) so that it can be migrated easily.

Thanks, that looks cool. I don't really have any influence over the developers but I'll pass it along. The president's only concern is raising the stock, not getting it written properly...

> **windependence said:**
> [http://www.kofler.cc/mysql/mssql2mysql.html](http://www.kofler.cc/mysql/mssql2mysql.html)

-Tim

I'm not looking for a way to convert a pre-existing database. There are tons of online tutorials for that... Thanks anyway.

---

