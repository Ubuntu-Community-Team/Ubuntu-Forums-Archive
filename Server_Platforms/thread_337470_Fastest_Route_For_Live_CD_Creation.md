---
title: "Fastest Route For Live CD Creation"
date: 2007-01-13
forum: Server Platforms
---

### Post by SuperMike on 2007-01-13
Let's say I have a PHP/PostgreSQL web app that works okay on Ubuntu Server, and I want to make a LiveCD for customers to try it out. Besides all the 'apt-get --purge remove' commands I would type to strip out those things I don't want, I would probably add:

'ne' text editor
php5
apache2
postgresql
phpPgadmin
webmin
cool new Tiger interface for webmin
some bootsplash stuff
a custom firewall script

What's the path of least resistance (time-wise) for creating a live CD of a customized Ubuntu Server?

---

### Post by depele on 2008-03-08
Reconstructor is a good option

I managed to install apache, php, phpmyadmin, 

But someway webmin always gives a users error when I try to log in.

You can try to implement all of them using the commandline from reconstructor.

---

