---
title: "need help to setup LAMP server and replication database to slave server"
date: 2012-05-27
forum: Server Platforms
---

### Post by bhadreshsakariya on 2012-05-27
Hello all,
i am new to linux world, i would to establish LAMP server(Local, UAT server and Production server)and replicate database to slave database server within 1 seconds(without any error) and how can i check Identify which pages / contents / queries are consuming more resources , fine tuning the components.

hope someone can provide me a right direction to setup a server or provide links for setup a server.

Thanks in advance.

---

### Post by SeijiSensei on 2012-05-27
Unless it's impossible to convert your application from MySQL to PostgreSQL, I'd strongly suggest considering the latter.  PG [9.0]("wiki.postgresql.org/wiki/Binary_Replication_Tutorial") now has pretty extensive replication facilities which have apparently been improved in [PostgreSQL 9.1]("http://www.postgresql.org/docs/9.1/static/warm-standby.html").

If your application makes database requests via an API of some sort like PEAR-DB or, as in my case, self-written libraries, then converting from one database system to another may not be too difficult.  If there are a lot of hand-coded MySQL query strings, or queries that use some idiosyncratic MySQL syntax, conversion will be a more difficult task.

If you're looking for "enterprise-class" features like replication in an open-source database, I'd use PostgreSQL.  Strategically, PG's target is Oracle itself, not MySQL.  I doubt Oracle has any interest in seeing MySQL displace commercial Oracle DBMS installation on corporate systems.

---

### Post by bhadreshsakariya on 2012-05-28
> **SeijiSensei said:**
> Unless it's impossible to convert your application from MySQL to PostgreSQL, I'd strongly suggest considering the latter.  PG [9.0]("wiki.postgresql.org/wiki/Binary_Replication_Tutorial") now has pretty extensive replication facilities which have apparently been improved in [PostgreSQL 9.1]("http://www.postgresql.org/docs/9.1/static/warm-standby.html").

If your application makes database requests via an API of some sort like PEAR-DB or, as in my case, self-written libraries, then converting from one database system to another may not be too difficult.  If there are a lot of hand-coded MySQL query strings, or queries that use some idiosyncratic MySQL syntax, conversion will be a more difficult task.

If you're looking for "enterprise-class" features like replication in an open-source database, I'd use PostgreSQL.  Strategically, PG's target is Oracle itself, not MySQL.  I doubt Oracle has any interest in seeing MySQL displace commercial Oracle DBMS installation on corporate systems.

Thanks for response, but the application has hand-coded MySQL queries so cann't use PG(may be in future).

could you please tell me some simple step by step guide for mysql replication on slave server.

Thanks a lot in advance.

---

