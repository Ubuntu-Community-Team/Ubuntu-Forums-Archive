---
title: "Reduce waiting time"
date: 2012-11-26
forum: Server Platforms
---

### Post by hunterlove22 on 2012-11-26
Hello,

I am trying to reduce waiting time for server. I tried to use both nginx and apache, but waiting is till the same. Please take a look at the picture:

[IMG]http://i47.tinypic.com/34nof2u.png[/IMG]

Please tell me how to reduce it. I am thinking problem is also related to MySQL.

Thanks

---

### Post by spynappels on 2012-11-26
If changing the web server made little or no difference, I'd be looking elsewhere, either in your PHP code, or in the MySQL database design or query structure. I've never seen a server take 4 seconds to respond, even with highly complex databases and queries with multiple joins, so I'd look for error messages involving both PHP and MySQL first.

Sorry I can't be of more help.

---

### Post by SeijiSensei on 2012-11-28
Have you tested the performance of the queries you are using in PHP?  Usually performance problems in SQL lies in poorly-indexed databases.  Have you indexed every field in the database on which searches might be conducted?  If you have SELECTs that employ multiple criteria, have you constructed the appropriate indexes using all the criteria?

Use the command-line mysql client and run every query in the application against the database manually.  Do some of them take a long time to execute?  Check the indexing on those queries.

---

### Post by rubylaser on 2012-11-28
What does your YSlow grade look like in each category?  I'm seeing a whole bunch of GET requests on that list (and I can't see all of it).  Have you minified your Javascript, Sprited and minimized  images, etc.  Reducing the size and [number of requests]("http://developer.yahoo.com/performance/rules.html#num_http") can have a MASSIVE impact on page loading speeds.

You could look into your queries with MySQL EXPLAIN to ensure you have properly indexed fields, and the scope of your queries aren't grabbing a bunch of unnecessary items. Also, depending your your program, you may be doing individual queries for each dynamic object rather than rolling them into one single SELECT.

---

