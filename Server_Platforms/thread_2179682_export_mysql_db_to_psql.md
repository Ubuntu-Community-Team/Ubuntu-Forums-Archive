---
title: "export mysql db to psql"
date: 2013-10-09
forum: Server Platforms
---

### Post by bewareofthephog on 2013-10-09
I have a database in mysql, I'd like to export it and load it into psql, is there an easy method to do this?

---

### Post by SeijiSensei on 2013-10-09
Well, it's not entirely "easy," but if you use mysqldump to create a plain-text version of the database, you can massage the commands it creates to fit the PostgreSQL syntax.  It depends a lot on how complex your database is.  If it's largely just tables, you'll end up with a bunch of CREATE TABLE commands that are pretty simple to transfer.  If you have lots of indexes, triggers, stored procedures, etc., it might be a bit more demanding.

Another option is to use a program like Microsoft Access that can connect to both databases using ODBC.  Then you can create the corresponding empty tables in PG before beginning and use Access to copy their contents from one DB to the other.  Again you'll probably have to create things like stored procedures manually.  Libre/OpenOffice Base can do this too, but I find it much more clunky to use than Access.

---

