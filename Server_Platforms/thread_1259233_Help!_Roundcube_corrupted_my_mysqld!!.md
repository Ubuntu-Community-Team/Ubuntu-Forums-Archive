---
title: "Help! Roundcube corrupted my mysqld!!"
date: 2009-09-06
forum: Server Platforms
---

### Post by artheus on 2009-09-06
Hi! I've had my server for some time now.. and I felt the need to install roundcube on it.. so I could read my mail from anywhere, without opening unnecessary ports to my server... So I started installing, and at first it seemed like everything was ok.. It made a new database in mysql, and It seemed to connect really nice.
Then I made the connection to apache via the apache.conf file in /etc/roundcube, I went to a browser and browsed to [www.mydomain.com/roundcube](www.mydomain.com/roundcube). But! When I got to the site it told me it couldn't make a connection to the mysql database.. So I used "sudo dpkg-reconfigure roundcube-core" to reconfig the database.. Still the same problem.. I went through the process a couple of more times, to see if there where something I missed. But I couldn't really see no errors. Until the last time I reconfigured.
Then a new error came up. "There was a problem connecting to the mysql database" in the dpkg-reconfigure screen!!

So the I tried to connect to my database using phpmyadmin, didn't work.. None of my regular users could access it!
I tried via my server to "mysql -u user -p" but not a chance!!
The error code I get when I do that is
```
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
```

What has happened to my mysql?? Is there a chance I can save all the data in the databases!?!? It's reaaally important data!

Hoping for the solution!

//Artheus

---

### Post by artheus on 2009-09-06
The problem has changed form now.. like transformers or something..

I stopped the mysqld and used mysqld_safe and changed root password and stuff... And killed the mysqld_safe and started the mysqld again.. It worked for about 3 minutes, and then it stopped working and now it says that mysqladmin can't connect to server "localhost" and I can't stop the process.. even if I reboot the problem is still there.. I can't re-install, due to that I can't kill the mysqld..

What can I do?

---

### Post by hessiess on 2009-09-06
> **artheus said:**
> The problem has changed form now.. like transformers or something..

I stopped the mysqld and used mysqld_safe and changed root password and stuff... And killed the mysqld_safe and started the mysqld again.. It worked for about 3 minutes, and then it stopped working and now it says that mysqladmin can't connect to server "localhost" and I can't stop the process.. even if I reboot the problem is still there.. I can't re-install, due to that I can't kill the mysqld..

What can I do?

```

/etc/init.d/mysqld stop

```

?

---

### Post by artheus on 2009-09-06
Thanks! but no..
That was actually what I was trying, It just returned [fail] every time...

Just now I found the solution for the whole thing..

I used "killall mysqld" and it killed the mysql process.
Then I had to use "apt-get remove --purge mysql-server-5.0" and then use "apt-get install mysql-server-5.0" And now it works just fine again.

(No data lost in the database either :D)

Just a mystery failure..

Cheers,
Artheus

---

