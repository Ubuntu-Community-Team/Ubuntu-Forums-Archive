---
title: "separate apache - mysql"
date: 2012-02-01
forum: Server Platforms
---

### Post by geniegl on 2012-02-01
Hello everybody

on Server 1 (Apache with mono):

we have installed apache, we can see it on a browser that works :) thats okey. we install mono and mono_connector

On Server 2 (mysql):

we installed mysql, we create small simple database at first, the name of database we create is "artists.aspx"

Problem:

after we use commandline "gacutil -i /path/to/unzipped/connector/bin/MySQL.Data.dll" and in web.conf we change little bit by adding "<add assembly="MySql.Data"/>"  and try to go to [http://localhost/artists.aspx](http://localhost/artists.aspx) and it does work.

can someone help me in this, thanks :KS

---

### Post by directhex on 2012-02-01
Can you confirm that you can talk to the MySQL server across the network? i.e. "mysql -H server2" works?

---

