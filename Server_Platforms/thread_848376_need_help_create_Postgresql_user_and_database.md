---
title: "need help create Postgresql user and database"
date: 2008-07-03
forum: Server Platforms
---

### Post by Brazen on 2008-07-03
I just did a fresh install of Postgresql 7.4.16.  I've never used Postgresql before today.  I need to create a database and a user and give that user full access to that database.

From reading the documentation, this is what I thought I needed to do:

> # sudo su - postgres
-bash-3.00$ createuser -A -d -P -E testuser
Enter password for new user:
Enter it again:
CREATE USER
-bash-3.00$ createdb testdb -U testuser
createdb: could not connect to database template1: FATAL:  IDENT authentication failed for user "testuser"
-bash-3.00$

As you can see, I get an error.  And I'm not even sure if I'm going about this the right way.  Any guidance would be appreciated.

---

