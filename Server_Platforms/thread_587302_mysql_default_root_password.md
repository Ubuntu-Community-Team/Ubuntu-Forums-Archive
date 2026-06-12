---
title: "mysql default root password"
date: 2007-10-22
forum: Server Platforms
---

### Post by alsehendo34 on 2007-10-22
mysql asministrator cant make connection to database after I installed mysql with add remove applications.  

Ping works OK.

The two processes are running

Access denied for user 'root'@'localhost' (using password: NO)

Shouldn't grant be allowed to user root following new installation, if not what do they set the root password to.  Is the Ubuntu install different?

Yes I tried connecting via a terminal session as super user--same problem.

---

### Post by tehfatguy on 2007-10-22
Yeah, I am currently having the same problem... I would love to know how to fix this, as I can't even connect to my MySQL remotly, unless using PHPMyAdmin.

---

### Post by SjRaptor on 2007-10-23
you want to run the following:
```
$ mysqladmin -u root password *password*
```

and in case you haven't already,
```
$ mysql_install_db
```

---

### Post by alsehendo34 on 2007-10-23
run
"mysqladmin -u root password password"

tried it, I get the same error

---

### Post by alsehendo34 on 2007-10-23
I am original poster

I killed -9 the two mysql processes

deinstalled all with Synaptic Package Manager

installed client as root in terminal window
apt-get install mysql-client-5.0

installed server as root in terminal window
apt-get install mysql-server-5.0

changed the root password
mysqladmin -u root password "my_password"

Now it all works :)

---

### Post by ablondeau on 2007-12-18
To access mysql for the first time I tried username = "root" and for the password I entered my host machine's root password (the one I would have to use for sudo) and it worked.

---

