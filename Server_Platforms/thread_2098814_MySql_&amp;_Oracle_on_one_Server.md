---
title: "MySql &amp; Oracle on one Server"
date: 2012-12-27
forum: Server Platforms
---

### Post by TorMike on 2012-12-27
I've just installed ubuntu 12.04 64 bit on my machine.  I have not installed LAMP.
This machine will be a test bed and I need to install Oracle 11g.  

My question is simple.  Can I install and run both MySql and Oracle on the same server?

Are there know confib issues with apache2 whilst running 2 databases running on the machine?

I have another machine (32bit) running ubuntu serve 12.04 and MySQL.

---

### Post by SeijiSensei on 2012-12-27
I've run PostgreSQL on a machine with Oracle installed, and both MySQL and PostgreSQL on the same machine.

The daemon processes all listen on different TCP ports so they do not interfere with each other.

Apache doesn't talk to SQL servers at all.  Perhaps you're thinking about something like a PHP application?  You can open multiple DB connections in PHP to different databases and servers.  You simply need to include the "handle" that points to the database in which the query must be run.

---

### Post by TorMike on 2012-12-27
Ya, sorry, I should have been a bit more detailed.

My apps are written in PHP and open sessions with an Oracle DB, hence the question about Apache.

Seems there are no problems.

Great.  Thanks for the response.

---

