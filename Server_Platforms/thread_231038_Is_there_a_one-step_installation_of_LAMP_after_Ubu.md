---
title: "Is there a one-step installation of LAMP after Ubuntu server has been installed?"
date: 2006-08-06
forum: Server Platforms
---

### Post by Akhran on 2006-08-06
I did not install a LAMP server on initial installation. Now that the server is up, is it still possible to do a one-step installation of LAMP with aptitude?

Thanks!

---

### Post by sir_mud on 2006-08-06
Not sure about that, but theres always XAMPP from [SIZE=-1][COLOR=#008000]www.apachefriends.org/en/**xampp**.html[/COLOR][/SIZE]

---

### Post by cantormath on 2006-08-06
> **Akhran said:**
> I did not install a LAMP server on initial installation. Now that the server is up, is it still possible to do a one-step installation of LAMP with aptitude?

Thanks!

LAMP is Linux apache mysql php, so in synaptic or aptitude, I guess you could just select and install them.  I use Apache, Mysql and php 5.

However, you most likely will want to do some tuning.
[Here]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06") is a wonderful tutorial, with screenshots step-by-step, from start(install) to finish. I highly recommend you learn a little something while dealing with LAMP.

good luck...

---

### Post by az on 2006-08-06
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

No tuning required.  Just set a mysql root password and you are good to run your web application.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

If you prefer aptitude, just run

sudo aptitude install apache2 php5-mysql libapache2-mod-php5 mysql-server

All of those packages and their dependencies are in main.

---

### Post by mogwai on 2006-08-06
Not sure about aptitude, but apt-get:

sudo apt-get install apache2 php5 mysql-server php5-mysqli

If you want it, add phpmyadmin to that list as well.

---

### Post by cantormath on 2006-08-07
It doesnt get much simpler then this:
[http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06)

---

