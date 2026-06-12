---
title: "Need advice: How to link MS Access with PHP"
date: 2009-08-13
forum: The Cafe
---

### Post by Rackstar on 2009-08-13
Hi,

My father is software developer of a middle-sized industrial cleaning company. At the moment everything is done with MS Access (which my dad is used to)

Now he has got the assignment to let people see the progress of their orders on-line.

He asked me (PHP & MySQL developer) how to tackle this... 

How should we fix this? Does anybody have any experience with this sort of things. We have a server (Windows Server 2003) and static ip.

- Is it possible to migrate the DB to MySQL, and always use ODBC in MS Access?
- Is it possible to use PHP directly with the MS Access database?


Thanks!

---

### Post by Dragonbite on 2009-08-13
I'm not a PHP programmer but I think PHP can connect to Access somehow.

If you are using IIS, why not use ASP or ASP.NET?  It's already a part of Windows Server and ASP (or ASP Classic) is script based similar to PHP, if you don't want to go down that whole ASP.NET compile/etc. route.

Basically the tools are already all there for an ASP(.NET) environment already. I don't know how easy/difficult it is to set up a Windows Server to work with PHP.

I know it isn't very endearing to Linux, but it is a solution.

---

### Post by Tibuda on 2009-08-13
Use the [ODBC driver]("http://www.php.net/manual/en/ref.pdo-odbc.connection.php") for [PDO]("http://www.php.net/pdo").

If you are not using PDO, I really suggest you to start using it (or another database abstraction layer), because it will make your life a lot easier if you have to migrate your database. I prefer PDO because it is shipped with PHP since version 5.1.

---

### Post by thisllub on 2009-08-13
I don't know if there is a usable odbc driver for mySql but there is one for Firebird.
I built a system that way that had over 20GB of data in it.


[http://ibphoenix.com](http://ibphoenix.com)

---

### Post by Tibuda on 2009-08-13
> **Dragonbite said:**
> I don't know how easy/difficult it is to set up a Windows Server to work with PHP.
It is easy in both Apache and IIS. Not as easy as "sudo apt-get install libapache2-mod-php5", but it is easy.

---

### Post by Rackstar on 2009-08-13
> **danielrmt said:**
> Use the [ODBC driver]("http://www.php.net/manual/en/ref.pdo-odbc.connection.php") for [PDO]("http://www.php.net/pdo").

If you are not using PDO, I really suggest you to start using it (or another database abstraction layer), because it will make your life a lot easier if you have to migrate your database. I prefer PDO because it is shipped with PHP since version 5.1.

This was the answer I was looking for! Thanks, I think we'll go into this direction.

I will use PHP as I have a lot of PHPbooks and have a lot of experience with a framework, which I'm planning to use.

I hope I don't encounter too much bugs, as this is probably a feature that isn't used a lot.

---

