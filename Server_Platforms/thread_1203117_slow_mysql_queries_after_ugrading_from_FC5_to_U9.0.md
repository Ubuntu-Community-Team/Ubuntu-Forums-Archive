---
title: "slow mysql queries after ugrading from FC5 to U9.04 server"
date: 2009-07-02
forum: Server Platforms
---

### Post by agatek on 2009-07-02
I upgraded my old Fedora Core 5 server running mysql and php-mysql from 5.022 and 5.1.6 to 5.075 and 5.2.6 respectively and performance problems with accessing the databases appeared. At this point I am not sure what is the source but it seem to be rather related to php5-mysql than the mysql engine itself. This is how it shows up for a database of ~ 50k records:

Query: SELECT * FROM `zdjecie` WHERE 1 LIMIT 15000, 20000

1. The query executed via phpMyAdmin
FC5: 
Takes ~0.4s to execute and ~4s to start displaying the records

U9.04: 
Takes ~0.6s to execute and ~40s to start displaying the records.
Repeating the query SOMETIMES shorten this time to similar values as for FC5 so it looks like it is sometimes buffered.

2. Same query from the shell level:
mysql -u user --password=xxx db < query > /dev/null

takes a fraction of the second for both setups.

Anybody encountered anything similar or have some tuning suggestions?

---

