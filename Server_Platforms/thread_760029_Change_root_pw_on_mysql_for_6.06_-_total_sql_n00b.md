---
title: "Change root pw on mysql for 6.06 - total sql n00b"
date: 2008-04-19
forum: Server Platforms
---

### Post by lunaz on 2008-04-19
Tried to set the password for root according to this guide:
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/databases.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/databases.html)

Got to the configuration section and used

```

sudo mysqladmin -u root password PASSWORDHERE

```

then tried the next one
```

sudo mysqladmin -u root -h localhost password PASSWORDHERE

```

That gave an error like:
```

luna@teh-serverer:~/public_html$ sudo mysqladmin -u root password PASSWORDHERE
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

```

I tried using the server's ip address too but that didn't make a difference.

Some other guide said to comment that bind to 127.0.0.1 line in my.conf. I tried it both ways for no changes. I don't understand what that means... :P

Then tried to change it to a different one using:
```

sudo mysqladmin -u root -p OLDPASSWORD NEWPASSWORD
Enter password: 

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: YES)'

```

I'm using 6.06 LAMP command line version.
SQL is off right now hah..

---

### Post by conjur3r on 2008-04-19
Doesn't seem like mysql was running.  I'm not totally sure what the startup script is but it should be something along the lines of:

# sudo /etc/init.d/mysql start

---

### Post by lunaz on 2008-04-19
I fixed it, I think:

```

sudo aptitude remove --purge mysql-server
....stuff....

sudo aptitude install mysql-server
....stuff....

```

The reconfigurator thing asked a few questions and I chose Internet Site at the postfix config thing. **What does postfix have to do with mysql?**

Was able to set a password & login/out.
```

mysqladmin -u root password *******************
sudo /etc/init.d/mysql restart
mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 8 to server version: 5.0.22-Debian_0ubuntu6.06.9-log

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> \q
Bye

```

---

