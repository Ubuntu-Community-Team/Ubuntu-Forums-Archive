---
title: "Noob help with LAMP and MySQL"
date: 2010-02-07
forum: Server Platforms
---

### Post by TheAlien on 2010-02-07
Now Apache and PHP is running fine and work well. :)

The only problem is that my web applications that require a database all give me *Access Denied* when they try to access the MySQL database.

I've created a database and a user like this:

```
mysql> CREATE DATABASE database1;
``````
mysql> GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, INDEX, ALTER, CREATE TEMPORARY TABLES, LOCK TABLES ON database1.* TO 'yourusername'@'localhost' IDENTIFIED BY 'yourpassword';
```And I've entered the correct database name, user name and password.

Any sort of help is appreciated! I just don't know where to go from here.

---

### Post by mushwars on 2010-02-07
```
sudo apt-get install phpmyadmin
```

then go to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)


it will be the best decision you have ever made.

---

### Post by TheAlien on 2010-02-07
mushwars, will that solve my MySQL problem?

---

### Post by TheAlien on 2010-02-08
> **mushwars said:**
> ```
sudo apt-get install phpmyadmin
```then go to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)


it will be the best decision you have ever made.

That didn't turn out very well. That address didn't work. :(

---

### Post by gobbledigook on 2010-02-08
> **TheAlien said:**
> That didn't turn out very well. That address didn't work. :(

If you are connecting from a seperate pc then you need to use its ip address instead

---

### Post by wojox on 2010-02-08
Are you logged in as root when you do this:

```
mysql -u root -p
```

---

### Post by TheAlien on 2010-03-16
Sorry for the late reply! I just wanted to check back and tell that everything works fine now. I did some mistakes last time I tried, now on a fresh install the LAMP server with phpmyadmin works flawlessly!

I just love Ubuntu now! It's so darn easy to setup a webserver! :D

---

### Post by dudumomo on 2010-03-16
Yes quite easy indeed.
I hope a lot of people will be able to do so.

---

### Post by TheAlien on 2010-03-21
Is it safe to use straight out of the box?

I've read that you should change the PHP config file to a recommended version though.

---

