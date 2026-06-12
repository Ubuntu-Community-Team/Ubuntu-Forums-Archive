---
title: "cannot connect to database using MySQL Administrator"
date: 2008-04-14
forum: Server Platforms
---

### Post by cocotu on 2008-04-14
I got to fix what it says in this post: [http://ubuntuforums.org/showthread.php?t=693216](http://ubuntuforums.org/showthread.php?t=693216)
But then I get errors:
MySQL Error Number 1045
Access denied for user 'root'@'172.27.0.2'(using password: YES)
I'm able to ping the server.  I tried: mysql> GRANT ALL PRIVILEGES ON *.* TO ‘root’@’172.27.0.2';
and still same error.  I also did:
mysql> GRANT ALL PRIVILEGES ON *.* TO ‘root’@’%'
and same error.
suggestions? thanks’

---

### Post by cocotu on 2008-04-14
to my surprise it works without a password. now sure why.  I was reading this:[http://www.issociate.de/board/post/271830/Fw:_Install_MySQL_5.0_Error.html](http://www.issociate.de/board/post/271830/Fw:_Install_MySQL_5.0_Error.html) and they say that the default install doesn't have a password, but when I installed this LAMP server I set up a password for MySQL and the only way i'm able to login to mysql at the terminail is using a password: "mysql -u root -p" NOT "mysql -u root" as they say.  Is this a security issue? that even when you have set up a password at your LAMP server someone using MySQL Administrator can gain access to your databases? this is bad.

---

### Post by Deathrend on 2008-04-15
If you want to set a password, use 

```

set password for  'root'@'localhost' = password('<password>');

```

And the only way to access the database using outside programs (Like PHPMyAdmin) is by already knowning the Database password.  Most logins are only accepted using "localhost" so it's highly unlikely that anyone would be able to log into the database externally anyway. That's also a good reson to use differnt logins with just enough access for your differnt apps.

---

### Post by cocotu on 2008-04-15
Deathrend, I know how to change passwords, but that is not the problem. >  but when I installed this LAMP server I set up a password for MySQL and the only way i'm able to login to mysql at the terminail is using a password: "mysql -u root -p" NOT "mysql -u root" as they say. We are using: [http://dev.mysql.com/downloads/gui-tools/5.0.html](http://dev.mysql.com/downloads/gui-tools/5.0.html) to access the MySQL database which HAS A PASSWORD. thanks

---

