---
title: "php with mysql"
date: 2008-03-19
forum: Server Platforms
---

### Post by shahansudu on 2008-03-19
Hi,
    I have installed apache2, mysql, php5. I can get php to work with apache but cant call mysql functions from a php script. How can I configure php5 to call mysql?
Thank you

---

### Post by AntoC on 2008-03-19
Hi have you ever tried XAMPP, I use it everyday and is easyer than installing the single components and configure them....

---

### Post by Dr Small on 2008-03-19
Xampp works like a breeze in a sail.
Follow my tutorial if you want, as it can do everything you need and is simple to setup and configure:
[http://php.8ez.com/drsmall/blog/?p=96](http://php.8ez.com/drsmall/blog/?p=96)

---

### Post by uberlinux on 2008-03-19
dadabik is another cool one

---

### Post by sowelie on 2008-03-19
If you don't want to use something like xampp, you need to compile with an additional switch.  When you configure php add the --with-mysql switch:

```
./configure --with-apxs2=/usr/local/apache2/bin/apxs --with-mysql
```

 If it complains about not being able to find mysql libs, make sure you have the mysql client libraries installed:

```
sudo aptitude install mysql-client
```

If it still complains, add the directory to the switch:

```
./configure --with-apxs2=/usr/local/apache2/bin/apxs --with-mysql=/usr/lib/mysql
```

---

