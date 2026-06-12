---
title: "move mysql database information completely ?"
date: 2009-09-19
forum: Server Platforms
---

### Post by Findarato on 2009-09-19
Hello everyone,

I have recently changed my webserver directory to get it working with dropbox (now my laptop and my desktop share the same development directory). What I would like to do now, is do the same thing with mysql. Which folder would I have to share between the two computers in order to share mysql data ?

Thank you very much in advance,

Findarato

---

### Post by falconindy on 2009-09-19
Data for mysql is in "/var/lib/mysql/". If you wanted to share the config, it's in "/usr/share/dbconfig-common/internal/mysql".

---

