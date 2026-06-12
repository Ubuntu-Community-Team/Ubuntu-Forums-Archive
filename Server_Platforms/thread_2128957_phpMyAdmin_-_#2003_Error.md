---
title: "phpMyAdmin - #2003 Error"
date: 2013-03-24
forum: Server Platforms
---

### Post by EmmEight on 2013-03-24
Error:
```

#2003 Cannot log in to the MySQL server

```


Installed apache2, mysql-server, and php5

I know phpmyadmin is working. When I go to myserver/phpmyadmin I reach the classic login page

But when I enter:

Username - "root"
Password - ""

I get the following error:

```
Login without a password is forbidden by configuration (see AllowNoPassword)
```

And when I enter the credentials I created,

I still get the #2003 error.

I am stumped.

Any help would be amazing!:)

---

### Post by EmmEight on 2013-03-25
These two commands are life savers!

Went through and reconfigured (with a little more caution this time) My problem was I had used TCP/IP to connect, wheras I should have used the unix socket.

```
sudo dpkg-reconfigure phpmyadmin

sudo dpkg-reconfigure mysql-server-5.5
```

Reconfigured with unix socket and presto, logged right in.

---

