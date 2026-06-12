---
title: "restoring a mysql db with same name"
date: 2009-05-25
forum: Server Platforms
---

### Post by lunaz on 2009-05-25
my friend helped me move my lamp/file server to another computer, and all is working fine so far except the wiki with my recipes... :(

for whatver reason it got all screwed up so i re installed phpmyadmin & mediawiki, but now can't restore the database. i get the following error:
```

Error

SQL query:

--
-- Database: `wikidb`
--
CREATE DATABASE `wikidb` DEFAULT CHARACTER SET latin1 COLLATE latin1_swedish_ci;

MySQL said: Documentation
#1007 - Can't create database 'wikidb'; database exists 
```

---

### Post by kvizz on 2009-05-25
why don't you just drop your old database from within phpmyadmin?

---

