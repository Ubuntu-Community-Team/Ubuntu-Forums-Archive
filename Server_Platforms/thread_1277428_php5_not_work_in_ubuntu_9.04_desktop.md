---
title: "php5 not work in ubuntu 9.04 desktop"
date: 2009-09-28
forum: Server Platforms
---

### Post by shamsat on 2009-09-28
Hi,
I install the ubuntu desktop 9.04 and then install the apache2 and php5, from the ubuntu 9.04 server and enabled the php5.conf and php5.load modules in /etc/apache2/mods-enabled but when i want to open the php files in the root document /var/www the firefox is asking what to do save it or open, it means the php5 is not working with the apache2 server, any one can help please?

---

### Post by credobyte on 2009-09-28
```
sudo apt-get install apache2 php5 libapache2-mod-php5 && sudo /etc/init.d/apache2 restart

```

---

### Post by shamsat on 2009-09-28
Hi credobyte!
Thanks for reply, this command solve the problem:
# apt-get install apache2 php5 libapache2-mod-php5 && sudo /etc/init.d/apache2 restart
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apache2 is already the newest version.
php5 is already the newest version.
libapache2-mod-php5 is already the newest version.
libapache2-mod-php5 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
 * Restarting web server apache2                                                 ... waiting ..                                                          [ OK ]

---

