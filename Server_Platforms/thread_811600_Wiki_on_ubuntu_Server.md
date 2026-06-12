---
title: "Wiki on ubuntu Server"
date: 2008-05-29
forum: Server Platforms
---

### Post by elektro_komesar on 2008-05-29
Hi everybody,
I have installed Ubuntu server, apache2 web server, Tomcat5.5 and MySql 5.0.
I deploy several web sites on new environment and everything is working perfectly. However, my next issue is to move my company Wiki (I have web site and mysql DB transfered on ubuntu) from windows environment to ubuntu, and I can`t find any link about migration process. If anybody have such experience or have some link it would be very helpful to me.
thanks

---

### Post by heebus on 2008-05-29
You'll want to install PHP as well.  

I personally never had to do this, but it sounds trivial.  Do a mysqldump of the database on windows, then import it on the ubuntu server.  Place the web files on your new machine, e.g. /var/www/wiki.  Then browse to the machine [http://ubuntu-ip/wiki](http://ubuntu-ip/wiki).  

That should be all you need to do.

---

### Post by az on 2008-05-29
> **heebus said:**
> You'll want to install PHP as well.  

I personally never had to do this, but it sounds trivial.  Do a mysqldump of the database on windows, then import it on the ubuntu server.  Place the web files on your new machine, e.g. /var/www/wiki.  Then browse to the machine [http://ubuntu-ip/wiki](http://ubuntu-ip/wiki).  

That should be all you need to do.

You will need to add a site (or use the default site) in apache and have it point to the files for your web application (wiki).  Also, depending on the software, you will need to make your web application point to the new database (it may be named differently than on your windows box).

Anyhow, what wiki are you using?  The procedure should be similar to the regular set-up for that application.

---

### Post by elektro_komesar on 2008-05-29
thanks for reply,
Well, I`m not sure about Wiki (what Wiki is used?? How can I see that??). I literally copy web site from it`s directory in windows. Also, it uses MySql db on windows, so I make a backup of DB, and  restore it on ubuntu...so, DB is not a problem. What I can`t find is .config file where db connection was defined.
Also, some guidelines about php (what to install...) would be helpful.
Adding web site to apache should not be a problem, I already have one web site in apache directory (actually in /var/www/ ) so I have to add another virtual host.
What is matter to me is that php stuff and db connection.

---

### Post by elektro_komesar on 2008-05-30
Ok, I managed to solve my problem, so if anybody have same issue here what should do (transfering Wiki from Windows to Ubuntu server) I presume that MySql, Apache2 and php5 were installed:
1. backup wiki website from Windows environment, copy it to /var/www directory. (so you have now /var/www/wiki).
2. backup db from windows (in my case MySql - db backup  and then restore it) to Ubuntu Mysql.
3. edit VirtualHost (/etc/apache2/sites-available; copy default in same directory, name it according to wiki website directory and fix VirtualHost).
4. open in browser [http://localhost/wiki-website](http://localhost/wiki-website) for localhost, or [http://ip-address-or-domain-name/wiki-web-site](http://ip-address-or-domain-name/wiki-web-site)
follow the guide from browser and after few steps...your wiki is online on Ubuntu
regards

---

