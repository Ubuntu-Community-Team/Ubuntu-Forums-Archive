---
title: "Installing phpMyAdmin"
date: 2009-03-29
forum: Server Platforms
---

### Post by jackfranklin on 2009-03-29
Hey there,

I have installed php, mysql and apache and it all works succesfully. However I then typed in (from a friend's help)
 sudo apt-get install phpmyadmin 

And it all seems fine but now when I go to localhost/phpMyAdmin or localhost/phpmyadmin nothing happens.

Is there a good tutorial somewhere? And does the fact that I am on x86 matter?

Thanks!

---

### Post by hyper_ch on 2009-03-29
easiest way would be to include the path to phpmyadmin in the apache config

---

### Post by jackfranklin on 2009-03-29
Ok thanks, but how would I go about doing that? Sorry :P

---

### Post by hyper_ch on 2009-03-29
have a look at the alias directive in apache

---

### Post by kamaji792 on 2009-03-29
Hi,

My half-penny (that you can't get any more).

Does Apache work?

From memory, point your browser to:
```
http://localhost/
```

You should get a page that says

     "It Works!"

atb

:Edit:
The default directory for Apache (based on my Hard install) was:
/var/www
So I guess phpMyAdmin should be:
/var/www/phpMyAdmin
Just in case that helps :P

---

### Post by timboellis on 2009-03-29
This is how i setup apache SQL etc. if it helps


sudo apt-get install apache2
sudo apt-get install php5 libapache2-mod-php5
sudo apt-get install mysql-server
sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin
sudo /etc/init.d/apache2 restart

---

### Post by doogy2004 on 2009-03-29
just type [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

phpmyadmin is mapped to this location automatically when it is installed.

---

