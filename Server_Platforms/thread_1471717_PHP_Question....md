---
title: "PHP Question..."
date: 2010-05-03
forum: Server Platforms
---

### Post by Bradj47 on 2010-05-03
I installed Ubuntu Server edition 9.10 on my computer a few weeks ago. I successfully install GNOME and type **[http://localhost/](http://localhost/)** into Firefox and I get a page that says **It Works!** and tells me that Apache is working and all that. But when I put a directory full of PHP files under **/var/www/** and put **[http://localhost/foobar/](http://localhost/foobar/)** into Firefox, it asks me how I want to open a PHTML file. I never put a PHTML file in there. When I try **[http://localhost/foobar/index.php](http://localhost/foobar/index.php)**, it asks how I want to open the PHP file. Do I need to install PHP first or something? Shouldn't it automatically look at **index.php** when I type **[http://localhost/foobar/](http://localhost/foobar/)**? Sorry if these are n00b questions, I've never set up my own server before. I always just used free hosting online.

---

### Post by noway2 on 2010-05-03
Yes, you will need to install PHP.  You may also need to "tell" apache to parse .php files.  You may need to add index.php to your directory index in apache2.conf.

---

### Post by windependence on 2010-05-03
Edit the file /etc/apache2/mods-enabled/php5.conf: remove all # at line  Addtype for the types you want to run.

Install PHP:

```
sudo apt-get install libapache2-mod-php5
```

Run the following code in a terminal after you install PHP:
```
sudo a2enmod php5
```That should enable the php5 module in Apache. To restart Apache run:
```
sudo /etc/init.d/apache2 reload
```-Tim

---

### Post by madtom1999 on 2010-05-05
try replaceing localhost with 127.0.0.1

---

