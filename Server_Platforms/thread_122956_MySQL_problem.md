---
title: "MySQL problem"
date: 2006-01-28
forum: Server Platforms
---

### Post by Jedeye on 2006-01-28
Well im so close, well I think I am :)

First off I am still new to Linux and I have been trying to set my comp up as a web server, just for having fun with it, I got apache and php installed properly, and I think I have MySQL installed properly the only problem is I do not know how to set up my user name and password for MySQL

I searched around some and thought this would get it
```
mysqladmin -u root password db_user_password
```

but it leaves me with this

```
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: NO)'

```

Any ideas? im not sure if I accidently set a password while setting it up, I wouldnt even mind uninstalling and reinstalling it, but I dont know how to uninstall.

Please help the rookie :)

---

### Post by LordHunter317 on 2006-01-28
There should be no password if you didn't assign one.

---

### Post by weissed on 2006-02-22
First command means you changed the default blank password for user root to "db_user_password".

The error message probably comes from you not providing the **-p** option which means "the user HAS a password". Try this:
```
 $ mysql -u root -p
```
or 
```
 $ mysqladmin -u root -p status
```

---

### Post by Eternal Blade on 2006-02-23
I had a problem where I had to specify the host as 127.0.0.1.

If the solution above doesn't work try:

mysql -h 127.0.0.1 -u root -p

---

### Post by bbqbaker on 2006-02-26
i am having the same problem. is it possible to reinstall mysql?

---

