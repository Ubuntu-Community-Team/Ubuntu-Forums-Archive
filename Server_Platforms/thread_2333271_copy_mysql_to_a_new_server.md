---
title: "copy mysql to a new server"
date: 2016-08-08
forum: Server Platforms
---

### Post by Vegan on 2016-08-08
Ubuntu 16.04 will eventually fall out of support. Wordpress has backup and restore so there are options galore.

MySQL has a tool called mysqldump which can save the whole song and dance to a SQL file. Then this can be played back to MySQL and its ready to go.

[https://dev.mysql.com/doc/refman/5.7/en/copying-databases.html]("https://dev.mysql.com/doc/refman/5.7/en/copying-databases.html")

I like the idea of the simply dump from one server and feed it directly to the new server

shell> mysqldump db_name | mysql -h 'other_hostname' db_name

---

