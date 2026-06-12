---
title: "Can't set mySQL password"
date: 2006-08-11
forum: Server Platforms
---

### Post by stormblue on 2006-08-11
When I go to set mysql password I:

```
sudo mysqladmin -u root password newrootsqlpassword
``` and then hit enter and what shows up below it

```
sudo mysqladmin -u root password sudo apt-get upgradenewrootsqlpassword
```

I then type in my password when it asks for it and it gives me connect to server at localhost failed
error: 'access denied for user 'root'@'localhost' Using password NO

Any suggestions? Please help. Thanks.

---

### Post by az on 2006-08-11
> **stormblue said:**
> When I go to set mysql password I:

```
sudo mysqladmin -u root password newrootsqlpassword
``` and then hit enter and what shows up below it

```
sudo mysqladmin -u root password sudo apt-get upgradenewrootsqlpassword
```

I then type in my password when it asks for it and it gives me connect to server at localhost failed
error: 'access denied for user 'root'@'localhost' Using password NO

Any suggestions? Please help. Thanks.


1.  That error = WTF?
2.  "access denied for user 'root'@'localhost' Using password NO" means that there is already a password set and you must run
mysqladmin -u root -p password 
to use it.

---

### Post by mlind on 2006-08-11
Change to mysql user (or to that daemon user that manages mysql)
```

sudo su
su mysql

```

Then login to mysql database
```

mysql mysql
SET PASSWORD FOR root@localhost=PASSWORD('secrets');
flush privileges

```

---

### Post by stormblue on 2006-08-11
Can you tell me the command to issue to change my default root mysql password off a default fresh LAMP install.  I found this [http://doc.ubuntu.com/ubuntu/serverguide/C/databases.html]("http://doc.ubuntu.com/ubuntu/serverguide/C/databases.html")
and it says to do this:

```
sudo mysqladmin -u root password newrootsqlpassword
```

and then to connect using 

```
sudo mysqladmin -p -u root -h localhost password newrootsqlpassword
```

Correct?

Also is there any reason I couldn't have a password start with an exclamation point?

---

### Post by az on 2006-08-11
> **stormblue said:**
> Can you tell me the command to issue to change my default root mysql password off a default fresh LAMP install.  I found this [http://doc.ubuntu.com/ubuntu/serverguide/C/databases.html]("http://doc.ubuntu.com/ubuntu/serverguide/C/databases.html")
and it says to do this:

```
sudo mysqladmin -u root password newrootsqlpassword
```

and then to connect using 

```
sudo mysqladmin -p -u root -h localhost password newrootsqlpassword
```

Correct?



By default, it is not set.

The error mentioned indicates that one is set, or that something else is terribly wrong.  That message you got is fishy.  Hardware problems?  Corrupt filesystem?

---

### Post by stormblue on 2006-08-11
I figured something crazy was going on so I did a fresh install.  I haven't touched a thing, so if I follow those instructions I should be good to go correct?

---

### Post by az on 2006-08-11
> **stormblue said:**
> I figured something crazy was going on so I did a fresh install.  I haven't touched a thing, so if I follow those instructions I should be good to go correct?

Yup.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by stormblue on 2006-08-11
Works like a charm.  Now time to see if I can get SSH to work.

---

