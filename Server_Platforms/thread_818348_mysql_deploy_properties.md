---
title: "mysql deploy properties"
date: 2008-06-04
forum: Server Platforms
---

### Post by anderskitson on 2008-06-04
I have some deploy properties for a program that needs to be built. I need to modify them for mysql, the documentation mentions that mysql can be used but the drivers in the deploy properties file are for oracle. I have followed the steps in a previous post that I was asking for help [_[COLOR="Blue"]here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=787037"), In my documentation I found something mentioning this ***mysql-connector-java-3.1.13-bin.jar*** ,not sure how I would implement this, I have built the program once, but it doesn't seem to work, because the test web service that is supposed to show up in localhost is not there. The fields I have tried entering are 
> DB_DRIVER=org.gjt.mm.mysql.Driver
DB_DIALECT=org.hibernate.dialect.MySQLDialect
-----------------------------------------------------------------------
CSM_DB_DRIVER=org.gjt.mm.mysql.Driver

CSM_DB_DIALECT=org.hibernate.dialect.MySQLDialect


Also what does the ***csm*** part mean for the second pair of drivers.Any help would be greatly appreciated

---

