---
title: "LAMP-Mysql fresh install mistake"
date: 2009-03-21
forum: Server Platforms
---

### Post by nikolaos on 2009-03-21
I instaled the LAMP server packages (Apache, PHP, Mysql) from synaptic. Everything was ok except one thing, i (and ofcourse anyone) could connect to mysql simply by typing 

```
mysql
```

at the console!!!

I don't know if this usual or not, but i am posting to tell you how i got rid of it.

So, connect to mysql using the root account

```
mysql -u root -p
```

Use the mysql database

```
mysql> USE mysql
```

And finally delete all the entries from the user table, where the second column (User) is empty.

```
mysql> DELETE FROM user WHERE User='';
```

logout,

```
quit
```

and restart mysql.

```
sudo invoke-rc.d mysql restart
```

All should be ok now, if you try to run mysql just by typing mysql an error will occur.

---

### Post by cariboo on 2009-03-21
You are prompted to set a mysql password during install, you should set it there. A quicker way to do what you did is to run:

```
sudo dpkg--reconfiure mysql-server-5X
```

This allows to create a password for mysql.

Jim

---

### Post by nikolaos on 2009-03-22
The password you are prompted to create is the root password, it is valid ONLY for the

```
mysql -u root -p
```

login. It doesn't solve the problem. The empty "" named User still has access.

---

