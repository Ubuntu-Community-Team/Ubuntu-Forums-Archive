---
title: "apache2-mpm-perchild and php problems"
date: 2005-05-16
forum: Server Platforms
---

### Post by BigBadaBoom on 2005-05-16
Hi! I'm currently running an apache2 on my ubuntu server with the following modules installed:
```
apache2-mpm-prefork
apache2-prefork-dev
libapache2-mod-php4
php4-dev
php4-mysql
php4-pear
phpmyadmin
```

It works perfectly and does exactly what I want/expect it to do. Now a problem's come up though. I need one VirtualHost to run its php scripts as a different user.
I wanted to switch over to the apache2-mpm-perchild module since I found out that with that you can define the user and the group the php scripts are executed as for each VirtualHost and not just the entire server like with prefork.

When installing via apt-get it removes the php modules aswell though (they're dependent on prefork), and I just can't seem to get php to work again with perchild running.

Can anyone tell me what I'm doing wrong, what I have to do to get it to work (please don't tell me I have to compile php or install it with something else than apt-get... I'm not that good) or even better some other (easy ;)) way to execute some php scripts (well - one single site to be precise) as a different user.

Thanks a million in advance!
- BBB

---

### Post by LordHunter317 on 2005-05-17
[QUOTE=BigBadaBoom]Hi! I'm currently running an apache2 on my ubuntu server with the following modules installed:
```
apache2-mpm-prefork
apache2-prefork-dev
libapache2-mod-php4
php4-dev
php4-mysql
php4-pear
phpmyadmin
```

It works perfectly and does exactly what I want/expect it to do. Now a problem's come up though. I need one VirtualHost to run its php scripts as a different user.
I wanted to switch over to the apache2-mpm-perchild module since I found out that with that you can define the user and the group the php scripts are executed as for each VirtualHost and not just the entire server like with prefork.

When installing via apt-get it removes the php modules aswell though (they're dependent on prefork), and I just can't seem to get php to work again with perchild running.

Can anyone tell me what I'm doing wrong, what I have to do to get it to work (please don't tell me I have to compile php or install it with something else than apt-get... I'm not that good) or even better some other (easy ;)) way to execute some php scripts (well - one single site to be precise) as a different user.

Thanks a million in advance!
- BBB[/QUOTE]
 You can't use perchild with PHP4 as it's threaded and that's not a safe configuration.

If you have a seperate IP for this site, using a complete seperate Apache instance would be the eaisest way.

Failing that, the next best solution will probably be Apache suexec + PHP as a CGI script.

---

### Post by reformist on 2006-09-23
You can in fact run PHP4 or PHP5 with the threaded Apache. The packages on Ubuntu will not let you install mod-php and apache2-mpm-worker at the same time because mod-php5 is not compiled with experimental threading support -- Apache won't even load it. So, you have to compile PHP5 from source, which turns out to not be that difficult.

I've written a [detailed writeup](http://philisoft.com/blog/running-multi-threaded-apache-with-php-on-ubuntu/) for Ubuntu that might be helpful.

---

