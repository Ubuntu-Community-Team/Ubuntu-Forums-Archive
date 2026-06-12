---
title: "Drupal 5.16 installation problems"
date: 2009-03-31
forum: Server Platforms
---

### Post by blairm on 2009-03-31
Hi,

Decided to install drupal on my home machine to learn a bit more about it, but it's proving a little more difficult than I expected.
I followed instructions for Ubuntu Hardy on the drupal site and think 5.16 is installed - at least, got a long list of drupal themes etc scrolling past in the command line. Apache seems to be working - when I go to localhost in the browser I get the "It works!" message.
But where do I go from here? From reading, I thought there should be a screen in the browser allowing the creation of a database.
Do I need to download more stuff in order to access drupal or am I missing something really obvious?

Cheers,

Blair

---

### Post by kvizz on 2009-03-31
i guess you should type something like [http://localhost/drupal](http://localhost/drupal) (or another directory in /var/www you placed your drupal installation) in your browser, or make some changes to httpd.conf or to default site in /etc/apache2/sites-available/default

---

### Post by rodneymillerpca on 2009-04-01
I personal use Drupal and recommend first you use version 6.10 before you even start. Here is the perfect help for you [https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal) I'll be glad to help you with any thing I can if you still need assistance.

---

### Post by blairm on 2009-04-01
Thanks for your advice - will have another go tomorrow morning. Will get this working if it kills me!

Blair

---

### Post by blairm on 2009-04-01
Hi,

Tried following the how-to recommended above again - actually it was one of the first I tried, but I made little progress with it.
Problem appears to be with MySQL: when I try to set a password for MySQL I get the following:

blairm@orpheus:~$ mysql -u root
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Tried using root and the sudo password on my machine and the result was the same.

Any advice would be appreciated!

Cheers,

Blair

---

