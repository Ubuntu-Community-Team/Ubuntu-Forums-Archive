---
title: "LAP &amp; LM (as in LAMP)"
date: 2012-01-13
forum: Server Platforms
---

### Post by a2j on 2012-01-13
Thinking about separating apache+php and mysql on two different virtual servers. Is this a good idea? Possibly multiple apache+php servers connecting to a single mysql server.

---

### Post by SeijiSensei on 2012-01-14
> **a2j said:**
> Thinking about separating apache+php and mysql on two different virtual servers. Is this a good idea? Possibly multiple apache+php servers connecting to a single mysql server.

Only if the MySQL server is reliable enough; otherwise it constitutes a "single point of failure" that will take down all the sites that use it.  Apache+PHP isn't really very resource intensive.  Does the current server display high load averages just from serving web pages?  Do your sites exhibit unreasonable delays?

That said, I wouldn't have a problem doing this with one of my [Linode]("http://www.linode.com/") VMs since they've been rock-solid for months now.  I also spend the extra few bucks a month to create snapshot backups every night just for the warm and fuzzy feeling they provide.

If you run sites that use session cookies to track users, you'll have to ensure that PHP uses the database to store the cookie information if you have multiple front-ends. Otherwise the session information won't be available if server 1 answers the original request, then server 2 answers the next one.  This can happen if you use round-robin DNS to distribute the load across the front ends.

---

### Post by CharlesA on 2012-01-14
It might be good for separation of services - like if your apache server gets owned, your databases would be ok.

It might be a bit of a pain to configure, and as, Seiji said, single point of failure would be the SQL server.

---

### Post by Dangertux on 2012-01-14
I would consider using a failover DBMS but separating them isn't a bad idea multiple sites into one DBMS can cause problems though.

---

