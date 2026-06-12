---
title: "PHP performance"
date: 2016-09-30
forum: Server Platforms
---

### Post by PeterK2003 on 2016-09-30
Probably not the best place to post this but I don't know where to so...

I have some PHP scripts that run a lot longer than they should and i would like some sort that is free and not a huge pain to install that would give me something similar to an SQL execution plan so I can narrow down the problem spots.  

Does such a thing exist?

---

### Post by SeijiSensei on 2016-10-01
Are these scripts that query an SQL database?  If so, the problem is likely with the database design, not PHP.  Do you have indexes created for every possible combination of fields used in WHERE clauses?

Which SQL database are you using?  PostgreSQL, which I use almost exclusively, includes the [EXPLAIN]("https://wiki.postgresql.org/wiki/Using_EXPLAIN") command which can tell you which parts of a query are slowing down performance.  In general, though, I find creating the proper indexes has the biggest effect on query speed.

PHP by itself  is generally lightning fast.  It's very unlikely to be the source of the problem.

---

### Post by PeterK2003 on 2016-10-03
SOme of it is the SQL querry taking a while.  But the CPU on the web server takes a beating too so some of the blame has to be there.

---

### Post by SeijiSensei on 2016-10-03
Isn't that also just a symptom of the SQL server working hard on a complex query?

Have you run the command "top" to see which processes are taking up the computer's resources?  Open a terminal in one window, run "top", then open a slow page with your browser.  What processes jump to the top of the list?

---

### Post by PeterK2003 on 2016-10-03
the Apache process is the CPU hog.  The DB is on another server.

---

### Post by Vegan on 2016-10-03
there is a new release of MySQL out, not much can be done for Apache or IIS. Both have issues mostly due to GET and POST messages back and forth.

---

### Post by PeterK2003 on 2016-10-04
> **Vegan said:**
> not much can be done for Apache or IIS. Both have issues mostly due to GET and POST messages back and forth.

Can you elaborate?  It did seem to work better and then after an upgrade some time ago things seem to get noticeably worse.

---

### Post by SeijiSensei on 2016-10-04
I have to say I've never seen Apache be a CPU hog.  Now I'm not hosting sites that get hundreds or thousands of connections.  Are you?  Have any PHP pages that don't require SQL?  How do they fare?  

You are using the PHP module, /usr/lib/apache2/modules/libphp5.so from libapache2-mod-php5, rather than running PHP as a cgi executable, right?

---

### Post by PeterK2003 on 2016-10-04
> **SeijiSensei said:**
> You are using the PHP module, /usr/lib/apache2/modules/libphp5.so from libapache2-mod-php5, rather than running PHP as a cgi executable, right?

Pretty sure...How do I verify that?

I found that there was some mySQL update held back on the db sever which I forced to update and that seem to improve performance.  

I still see Apache getting pegged but it is for a much shorter time.

Thanks,
Peter

---

### Post by SeijiSensei on 2016-10-05
Do you have /usr/lib/apache2/modules/libphp5.so?  If you run "sudo apt-get install libapache2-mod-php5" apt should report that the package is already installed.

Glad to see that the update helped.  Now I'd start looking at queries and indexes.

---

### Post by PeterK2003 on 2016-10-05
i'm on php7 but yeah it is installed.  

Some of it is just going to be slow due to the number of rows being returned.  It is weather data so pretty much the only thing ever in the where clause is the date which is the primary key which would mean it is indexed by default correct?  Or do i need to index it separately?

---

### Post by SeijiSensei on 2016-10-05
Yes, it should be pretty quick if you're searching on the primary key.  How many rows are there in the database?  I've run queries against DBs with hundreds of thousands of rows in PostgreSQL and gotten back the results in a second or two if the query is well-indexed.  Is there anything else involved like postal codes or weather station IDs or the like?  If so, you should create indexes across field combinations like this:
```
create index wd_date_ID on weather_data_table (date,stationID);
```

---

### Post by PeterK2003 on 2016-10-06
It is only my weather station so there is no need for a station code.

There is 5,547,157 rows now.

---

### Post by SeijiSensei on 2016-10-06
I don't which SQL database you're using, but you should read the documentation on performance tuning for the one you're using.  Oftentimes the defaults are designed for smaller databases than yours like the ones that store content for web sites.

[MySQL](http://www.mysql.com/why-mysql/performance/)
[PostgreSQL](https://wiki.postgresql.org/wiki/Performance_Optimization)

Also how much memory does the DB server have?  The more memory, the less time it will spend running disk transactions.  Something like 8 or 16 GB of physical memory might help.

---

