---
title: "Tomcat Vs. Zend Platform: speed and reliability"
date: 2006-02-23
forum: Server Platforms
---

### Post by OneSeventeen on 2006-02-23
I want to make some scripts that process and store data a few thousand times per second, and I want it to be reliable, secure, fast, and reliable.  (and fast)

I like using Ubuntu as a server at my current job because it is easy, and has a great community, and nice prices on support, and wouldn't mind to continue using it, as long as it can handle some systems-critical application that would cost millions if it went down.  (no pressure, eh?)

Mainly meaning I want to be able to lock it down to only do exactly what it is intended to do, and also do all that fun clustering/mirroring/load balancing stuff, so if one building burns down, and the other looses power at the same time, the site hosted is still running happily.  (also making upgrading without interrupting services easier)

Any reccomendations on what would be quicker and more reliable to go with as far as the scripting language though?  (I hear Java Server Pages on Tomcat are supposed to be fast, but I've heard the same about encoded PHP5 scripts on the Zend platform... does anyone have experience with both or know some benchmarks?)

Also, is processing/storing/retrieving 2 or 3k transactions per second unreasonable, very easy, or moderately difficult?  I want to know how realistic I'm being, or if I'm worrying too much about something that should be simple using default PHP5/postgresql/apache2 installations.

---

### Post by LordHunter317 on 2006-02-23
> **OneSeventeen]I want to make some scripts that process and store data a few thousand times per second,[/quote]How much data?  Stored where?

> I like using Ubuntu as a server at my current job because it is easy, and has a great community, and nice prices on support, and wouldn't mind to continue using it, as long as it can handle some systems-critical application that would cost millions if it went down.  (no pressure, eh?)Ubuntu isn't for you then.  You can't get the support you want on the packages you need, likely, or under the terms you want.  But there's no way to be certain without details.

You also sound like you seriously like the experience to deploy an enterprise solution like this said:**
> Mainly meaning I want to be able to lock it down to only do exactly what it is intended to do, and also do all that fun clustering/mirroring/load balancing stuff, so if one building burns down, and the other looses power at the same time, the site hosted is still running happily.  (also making upgrading without interrupting services easier)This is dependent on the solution architecture, but not trivial no matter what path you take.

> Any reccomendations on what would be quicker and more reliable to go with as far as the scripting language though?  (I hear Java Server Pages on Tomcat are supposed to be fast, but I've heard the same about encoded PHP5 scripts on the Zend platform... does anyone have experience with both or know some benchmarks?)Of those?  None of the above will likely be adequate, but it depends on your solution architecture.  And is this a web application?

> Also, is processing/storing/retrieving 2 or 3k transactions per second unreasonable, very easy, or moderately difficult? Depends on how big a transaction is, but it's certainly something that will require real hardware, and a dedicated, meaty database server.

By real hardware I mean 4/8 processors, 8-16GiB, RAID-1 for OS/transaction logs, RAID-5/RAID-10 (depending on I/O content) for tables, possibly another array for indexes (again, depending on I/O content) minimum.  

Especially if the solution is clustered or replicated.

But, depending on what your implementing, you can get away with less.  Heavy read servers can go with less CPU and RAM for the DB, and use smaller (blades even) servers running memcached.

> I want to know how realistic I'm being, or if I'm worrying too much about something that should be simple using default PHP5/postgresql/apache2 installations.PostgreSQL clustering and failover is rather immature.  I wouldn't write anything serious or mission critical in PHP5 personally, as the language has a lot of terrible builtin limitations.  YMMV of course.

(More Details)

---

