---
title: "Using MySQL and PostgresQL"
date: 2008-10-03
forum: Server Platforms
---

### Post by R.Bucky on 2008-10-03
I am using a LAMP installation on my Ubuntu 7.10 box to host my personal web pages and others. I would like to install PostgreSQL to use as a database on the local drive only - not available via the web. The PostgreSQL database would hold personal info that I would not want to have the chance of being exploited on the web. Hence the reason for not wanting to use MySQL. 

Question: Can I have MySQL and PostgreSQL on the same box without confusing my web service?

---

### Post by lykwydchykyn on 2008-10-03
> **R.Bucky said:**
> I am using a LAMP installation on my Ubuntu 7.10 box to host my personal web pages and others. I would like to install PostgreSQL to use as a database on the local drive only - not available via the web. The PostgreSQL database would hold personal info that I would not want to have the chance of being exploited on the web. Hence the reason for not wanting to use MySQL. 

By default, postgres will only accept local connections.  However, if the server is accessible from the Internet, there is always the potential for some kind of exploit.  That's just reality.
> 
Question: Can I have MySQL and PostgreSQL on the same box without confusing my web service?

Absolutely.  They operate on different ports, and require different libraries and commands to access from PHP.

---

### Post by R.Bucky on 2008-10-03
> **lykwydchykyn said:**
> By default, postgres will only accept local connections.  However, if the server is accessible from the Internet, there is always the potential for some kind of exploit.  That's just reality.

I agree. If it is on your box, there is always some way to get at it form the net. If appreciate your quick reply. Thanks!

Mark

---

