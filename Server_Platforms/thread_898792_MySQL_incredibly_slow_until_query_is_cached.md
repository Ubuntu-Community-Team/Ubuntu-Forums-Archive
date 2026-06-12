---
title: "MySQL incredibly slow until query is cached"
date: 2008-08-23
forum: Server Platforms
---

### Post by rahashii on 2008-08-23
Hi everybody,

I'm having a weird MySQL issue. I have a PHP application that I've recently migrated to Hardy Heron. The application is highly MySQL-intensive (it executes 10 select queries about 50 times each to compile the needed information for a report).

The problem I'm experiencing is that since the migration, the mysql query execution is EXTREMELY slow the first time through. After that, it runs quite quickly.

A look at `top` shows me that MySQL is using 100% of the CPU for the duration of the query execution. It takes about 4 minutes for the queries to complete. Once the queries have run (and presumably been cached by MySQL), it takes only about 4 seconds to run them again. This is true even as those queries change slightly, such as different values in the where clause.

I'm having a hard time finding anyone with a similar problem. 

I know a lot of people will be tempted to suggest that the problem lies in my queries themselves. That doesn't really follow, though. The tables are well-indexed, and none of the queries are particularly large or unwieldy. Most importantly, it has run perfectly for years on a server with one half the processors, 1/3 the clock speed, a 5th the RAM, etc (though it did take 30 seconds or so to complete).

I'm using the default MySQL version:  5.0.51a-3ubuntu5.1

Any ideas? 

Thanks

---

### Post by mbeach on 2008-08-23
yes, I was tempted, but I won't.  I would suggest looking at preparing and excuting the statement especially if are running the statement a bunch of times per page - but if one query is holding up the rest it may not make a difference.

I'd also recommend getting a copy and reading
[http://oreilly.com/catalog/9780596008949/toc.html](http://oreilly.com/catalog/9780596008949/toc.html)
Expand the "Strategy before Tactics" for a quick read of the type of book it is.  I'd highly recommend getting the book.

---

### Post by rahashii on 2008-08-23
mbeach,

Thanks for the reply. I know the book you're referring to. I own it in fact, and it is an excellent book. I'm afraid it's not going to be of much help in this instance, as the problem is a MySQL-specific one. In fact, it seems to be a build-specific issue at that. The script worked fine with an older build of MySQL. The problem only arose after moving the application to the newer ubuntu build of MySQL.

If the issue were bad database design or bad queries I doubt this application would have been working fine for the past 4 years as it has (it even ran on a Pentium II with 64MB of RAM originally). Something else is going on here.

---

### Post by wirepuller134 on 2008-08-24
What version of mysql was the application written to work with, if it was written with an older version it could cause problems resolving queries.  We have had customers whom run into this quite a bit.  We don't have the databases on the same server as the host files though.

---

### Post by rahashii on 2008-08-24
wirepuller134,

I believe it originally ran on MySQL 4.0. Most recently it has been running on MySQL 4.1.21. 

Thanks

---

### Post by mbeach on 2008-08-25
ok, misunderstood that.  I wonder then at the outset of that old server were some commands run to optimize for your tables.  I'm not a mysql guy (use it when the app being installed uses it) but I seem to remember an 'analyse table' command coming in handy for someone at one point, perhaps not in your case.  Not knowing if your data is changing all the time, used mostly for lookup etc hard to give any advice.  It seems you've got a good handle on it regardless.   Is there an mysql tool to show the execution plan - does it give any indication at least where the hold up is?  Good luck.  I would also look into the server settings - is there a limit of some sort being hit?  Is this a site with many users all hitting the db at the same time?  Is there a specific amount of time between calls to that page which yeild the long wait?  ie, if you view the report over and over for the first five minutes it runs quick, then takes a long time, then is good for another 5 minutes?  Is there a way to cache the offending query?  Sorry- not expecting the responses, just trying to think of the typical types of things I would look into (... informix background ...)

---

