---
title: "MySQL or PostgreSql?"
date: 2008-09-15
forum: Server Platforms
---

### Post by nonaguy on 2008-09-15
Hello, I was hoping I could get some advice for a little database issue I am facing. First a little background, we have approximately 198 Access Databases on the main network drive; we have decided to integrate all that data into a PostgreSQL database (mainly because PostgreSQL can use LDAP authentication). The issue we have is how to get all that data into the PostgreSQL database. We have come up with two options:

#1) Use the MySQL conversion toolkit to convert the mdb files in Access to tables that can be read by MySQL, then run a script to convert it all for PostgreSQL.

#2) Set up the data source to be PostgreSQL, and go into Access to move the tables to PostgreSQL. 

We are debating which move will be easiest for us to implement. Does anyone have any experience with this kind of problem?

*oops, I should have put more thought into the title, it is very misleading, sorry.

---

