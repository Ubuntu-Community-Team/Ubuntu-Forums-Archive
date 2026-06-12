---
title: "Trouble Launching MySQL 5.1 on Ubuntu 9.04 Server Edition"
date: 2009-10-18
forum: Server Platforms
---

### Post by DBGrind on 2009-10-18
Hello,

Noob here.  I am having problems launching MySQL on by Ubuntu Server Edition 9.04.  I did the install with the LAMP.

Whenever I try to create a DB using 'mysqladmin create *databasename, *I get the error:
[COLOR=Red] mysqladmin: connect to server at ‘localhost’ failed
error: ‘Access denied for user ‘honey’@'localhost’ (using password: NO)’

[COLOR=Black]FYI, Currently I dont have any interent/network connections going to this server; at the moment all I need to do is the create new DB and its subsequent tables.  I plan to utilize the networking aspects at a later date.

Any help is much appreciated.

Thank you.
[/COLOR][/COLOR]

---

### Post by nandemonai on 2009-10-18
> **DBGrind said:**
> Hello,

Noob here.  I am having problems launching MySQL on by Ubuntu Server Edition 9.04.  I did the install with the LAMP.

Whenever I try to create a DB using 'mysqladmin create *databasename, *I get the error:
[COLOR=Red] mysqladmin: connect to server at ‘localhost’ failed
error: ‘Access denied for user ‘honey’@'localhost’ (using password: NO)’

[COLOR=Black]FYI, Currently I dont have any interent/network connections going to this server; at the moment all I need to do is the create new DB and its subsequent tables.  I plan to utilize the networking aspects at a later date.

Any help is much appreciated.

Thank you.
[/COLOR][/COLOR]


You need to use the password you setup when you installed mysql.

```
man mysqladmin
```

;)

---

### Post by karlson on 2009-10-19
> **DBGrind said:**
> Hello,

Noob here.  I am having problems launching MySQL on by Ubuntu Server Edition 9.04.  I did the install with the LAMP.

Whenever I try to create a DB using 'mysqladmin create *databasename, *I get the error:
[COLOR=Red] mysqladmin: connect to server at ‘localhost’ failed
error: ‘Access denied for user ‘honey’@'localhost’ (using password: NO)’

[COLOR=Black]FYI, Currently I dont have any interent/network connections going to this server; at the moment all I need to do is the create new DB and its subsequent tables.  I plan to utilize the networking aspects at a later date.

Any help is much appreciated.

Thank you.
[/COLOR][/COLOR]

Until you set up user 'honey' as with admin privileges in the database you won't be able to run mysqladmin, etc.

You can do one of 2 things:

1.  Become root and run this command.
2.  run: ```
mysql -u root
```.  Then run ```
create database
``` command.

---

