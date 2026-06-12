---
title: "Inaccessible Web Folder"
date: 2010-05-13
forum: Server Platforms
---

### Post by Gerbilkit on 2010-05-13
I recently obtained an old dell desktop computer, 2.8 GHz Pentium 4 1 GB ram, 40 GB HD etc.  And I am trying to convert it into a personal server/sandbox for my development.  I used the instructions at this url to install Apache + php/mysql.
[http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-9.10-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-9.10-lamp)

Then I ran into problems.  Phpmyadmin installed, but when I went to localhost/phpmyadmin it wasn't there.  Also it seems my inded file is being stored in var/www, which is a protected read only folder.  I am unable to edit the files here, or even add new ones (outside of vi which I refuse to use unless absolutely necessary). I tried CHMODing to no avail.  Was this a bad method for setting up my server? Is there something I am missing that is really obvious? I'm pretty spoiled as in the past xampp windows installer did all the work for me, but I honestly didn't expect to have any problems with this.

---

### Post by windependence on 2010-05-14
What is the output of:

```
#ls -la /var/www
```

-Tim

---

### Post by cdenley on 2010-05-14
Run these commands, then post the output here.
```

cat /etc/apache2/conf.d/phpmyadmin.conf
sudo /etc/init.d/apache2 restart
echo -e "GET /phpmyadmin/ HTTP/1.0\n"|nc -q 1 127.0.0.1 80

```

By default, /var/www is owned by root. This is the most secure, but doesn't allow your user to modify the contents unless you first escalate to root privileges. There are many ways to do this.
```

gksu nautilus /var/www
sudo nano /var/www/index.html
gksu gedit /var/www/index.html

```
If necessary, you can give the admin group (which your default user belongs to) write permission for /var/www.
```

sudo chgrp -R admin /var/www
sudo chmod -R g+rwX /var/www

```

---

