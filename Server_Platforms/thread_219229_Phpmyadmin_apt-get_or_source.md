---
title: "Phpmyadmin: apt-get or source?"
date: 2006-07-19
forum: Server Platforms
---

### Post by wyth on 2006-07-19
I've been setting up my server, and things are all together, except when I try to run phpmyadmin.  I installed it via synaptic, but it installed in /usr/share rather than /var/www.  No problem, I made the symlink, but then I run into another problem --the header and footer of the interface aren't included (see screenshot).  

I'm just wondering if there's an easy fix for this, or if it has something to do with phpmyadmin installing in /usr/share rather than /var/www, and if so, would I be better off just installing it from source rather than synaptic.

---

### Post by az on 2006-07-20
That's not normal.  It works fine on a standard ubuntu LAMP stack.  A symlink is made in /var/www by the package installation.  What versions of apache, php and mysql are you using?

---

### Post by wyth on 2006-07-20
I'm using apache2, mysql client and server 5, and php 5.  

I went through the installation a few times, and kept getting the same results.  So I actually I removed phpmyadmin through apt and installed manually, configured the config.inc.php file and got things runnning that way, but I wouldn't mind knowing what's up for future reference.

---

### Post by az on 2006-07-20
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Install apache2 php5-mysql libapache2-mod-php5 mysql-server

and then enable universe and install phpmyadmin.  Works out of the box.  Browse localhost/phpmyadmin.

You can even set your mysql root password using phpmyadmin.

---

### Post by wyth on 2006-07-20
Thanks for the help, azz.  That's actually what I had done, and I have all of those packages installed.  I can't explain why, but when I installed phpmyadmin through synaptic --a few different trials --it never made the symlink, and when I made the symlink, that's when I'd get the goofy looking phpmyadmin interface through localhost.  Once I downloaded the phpmyadmin source and installed that, I got it going, and localhost and all that now works fine.  It does make me nervous that something else may be wrong, though.

---

