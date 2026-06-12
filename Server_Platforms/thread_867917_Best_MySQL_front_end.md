---
title: "Best MySQL front end?"
date: 2008-07-23
forum: Server Platforms
---

### Post by xylene2301 on 2008-07-23
Does anyone have an opinion as to the best MySQL front end tool currently available?  
I've looked at Emma and there's also kmysqladmin and maybe some others.

Thanks
Xylene

---

### Post by Endwin on 2008-07-23
Personally I like phpmyadmin.

---

### Post by windependence on 2008-07-23
I'll second that one. PHPmyadmin.

-Tim

---

### Post by raul_ on 2008-07-23
mysql-gui-tools

---

### Post by Jordanwb on 2008-07-23
+1 for phpmyadmin.

---

### Post by jdavis on 2008-07-23
another +1 for phpmyadmin

---

### Post by xylene2301 on 2008-07-23
I guess I should have specified that I need a mysql tool that will connect to multiple remote mysql servers.

phpmyadmin just admins databases on its own resident server, does it not?

Xylene

---

### Post by wirelessmonkey on 2008-07-23
Phpmyadmin can be configured to connect to remote mysql installations, so long as they are accessible from the server running phpmyadmin.

I also use Kmysqladmin, if you'd rather not use phpmyadmin.

---

### Post by imon9 on 2008-07-23
currently using navicat lite (free)
[http://www.navicat.com/download.html](http://www.navicat.com/download.html)

(run with java)

---

### Post by raul_ on 2008-07-23
> **xylene2301 said:**
> I guess I should have specified that I need a mysql tool that will connect to multiple remote mysql servers.

phpmyadmin just admins databases on its own resident server, does it not?

Xylene

mysql-gui-tools :)

the name says it all

---

### Post by tinny on 2008-07-24
phpmyadmin is really good for people who havent yet discovered [MySQL GUI Tools]("http://dev.mysql.com/downloads/gui-tools/5.0.html"). :p Also [MySQL Workbench]("http://dev.mysql.com/downloads/workbench/5.0.html") is available on Windows (Visual Database schema design application), will be available on Linux soon.

[DBDesgner4]("http://www.fabforce.net/dbdesigner4/") can be installed on Linux. MySQL Workbench is a fork of DBDesigner4 (Visual DB schema design).

---

### Post by trail.blazer on 2010-03-05
Navicat lite is also nice tool.

---

### Post by richardjh on 2010-03-05
I am going to be on my own in saying this but I prefer the mysql client. 

The one you get when you type

```
mysql - u db_user -p
```

and looks like 

```
mysql > 
```

Has all the features, easy to use, doesn't require a web server, ...

I have used Navicat, phpMyAdmin, mysql-navigator and possibly other long forgotten now.
I thought so... just me!

---

