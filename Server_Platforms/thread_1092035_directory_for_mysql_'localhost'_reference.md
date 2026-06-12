---
title: "directory for mysql 'localhost' reference?"
date: 2009-03-09
forum: Server Platforms
---

### Post by mojokorn on 2009-03-09
OK, here's a relatively simple one for an intermediate ubuntu user (which is not me)...

I'm developing a web app on an server with ubuntu and apache. I need to know where to put my db files so the 'localhost' servername reference in my php code will find them.  I tried the 'root', and the '/usr/share/mysql' with no joy.

Does anybody know?

](*,)

Thanks,

mojokorn

---

### Post by mrsteveman1 on 2009-03-10
I'm not sure what you mean, if you are connecting to mysql from a php application you don't need to worry about the storage of files on the disk, you only have to connect to the mysql daemon.

---

### Post by mojokorn on 2009-03-10
Steve,

Thanks for replying to this.

I was under the impression that the mysql_connect function actually connected to a file that resides on the server.  Is this correct?

From you description, it sounds like this function is connecting via some other method.  I would figure even the daemon would connect to sql files that reside on the server.  If so where do I put these files?

I've always relied on the phpMyAdmin to create the sql files and import data into them.  The server that I working on for this doesn't have the phpMyAdmin utility, so I have to do it manually.  This is new to me, so hence the confusion.

Any clarification, help you can give is greatly appreciated.

mojokorn

---

### Post by mrsteveman1 on 2009-03-10
Mysql connections are all done through the daemon, you should never have to create files or put them anywhere.

If you need to manually work on a database you can use the mysql commandline tool, documentation is available from Sun, but it's relatively simple.

You connect to the daemon by running:

> mysql -uroot -p

You will need to know the root password of course.

Then you can create a database like this:

> create database <name>;

Make sure you include the ; as that is what ends a statement.

The PHP website probably has documentation for how to connect to a mysql server daemon from PHP and manipulate databases.

---

### Post by mojokorn on 2009-03-11
Thanks! That definitely gets me started in the right direction.:)

---

