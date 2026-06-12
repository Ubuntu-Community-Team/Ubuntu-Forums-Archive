---
title: "phpmyadmin doesn't allow me to login"
date: 2014-03-21
forum: Server Platforms
---

### Post by deidara2 on 2014-03-21
Hello Community, 
 
I just rent my first root-server and never used linux before, so I got the following problem:
I made a new database through   phpmyadmin in mysql and imported some stuff in it. I realized, that I   need to allow external access because I had some data on a old server, I   needed on my new one. So I followed this tutorial to do this: [http://www.cyberciti.biz/tips/how-do...se-server.html]("http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html") .
After that I wrote "service mysql restart". And since then I can't login   into phpmyadmin anymore. I didn't changed any passwords or rights. I   already tried every password, I could imagine and tried every password   from my local password database, nothing works. 
Okay now I removed   phpmyadmin, mysql-common and mysql-server completely with purge and now when I try   installing phpmyadmin I get always this error: 
```
                 
[LIST=1]
[*]An error occurred while installing the database:                          &#9474;
 &#9474;                                                                           &#9474;
 &#9474; ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using      &#9474;
 &#9474; password: YES)                                                            &#9474;
 &#9474;                                                                           &#9474;
 &#9474; If at this point you choose "retry", you will be prompted with all the    &#9474;
 &#9474; configuration questions once more and another attempt will be made at     &#9474;
 &#9474; performing the operation. "retry (skip questions)" will immediately       &#9474;
 &#9474; attempt the operation again, skipping all questions.  If you choose       &#9474;
 &#9474; "abort", the operation will fail and you will need to downgrade,          &#9474;
 &#9474; reinstall, reconfigure this package, or otherwise manually intervene to   &#9474;
 &#9474; continue using it.  If you choose "ignore", the operation will continue,  &#9474;
 &#9474; ignoring further errors from dbconfig-common. 
[/LIST]

         

```
I can get to my phpmyadmin login screen but anyway the password doesn't  seem to work again, and I get this error, which I also got before I  removed it #1045 Cannot log in to the MySQL server" and this, which is  new, "Connection for controluser as defined in your configuration  failed."
I figured out, that I can login into MySQl through PuTTy, so terminal, but only when I click ENTER when it asks for a password. The strange thing is: I set up a password, when I installed MySQL. Maybe that's the error, because phpmyadmin doesn't allow no passwords?
Now I have no idea what to do next, hopefully one of you guys can help me. 
Ah and I run Ubuntu 64 bit 12.04.

Greetings Deidara

---

### Post by 7sbaV8Kt5PTh on 2014-03-21
Hi, Deidara.  If you deleted everything, including the database, you would have to recreate that.  You would also have to reassign the permissions in the DB for root.  I would login to mysql as the root user, and do a:

show databases;

Then use the 'grant all' syntax to add root and any other admin user to that database.

---

### Post by sandyd on 2014-03-21
Moved to server platforms

---

### Post by deidara2 on 2014-03-21
That's what I get, when I type in your commands:
```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| test               |
+--------------------+
2 rows in set (0.00 sec)

mysql> grant all
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 1


```

---

