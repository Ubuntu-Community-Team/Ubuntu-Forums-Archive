---
title: "MySQL/PHP Driven Home Inventory?"
date: 2007-08-22
forum: Server Platforms
---

### Post by 67comet on 2007-08-22
Hello, long time *nix'er (about 5 years via several distros) but not so hot with PHP or MySQL. I've recently started using MySQL a lot for implementation of Wordpress, Joomla, Xoom and an attempt at Plone. Needless to say I love it so far.

My wife recently asked me if I knew how she could catalog her music books (She's a piano teacher). She wants to be able to fire up her browser, hit her web site and search a plethora of ways for books and such. We run her web site (as well as several others) on a box turned server from our home. I am the admin for all that is her site in other words.

I'm not sure what would work as this, but I did just take a Database Concepts course (didn't do well at all) and think she is asking for a prime project for me to delve into building an actual useful tool for her.

Ideas on what a MySQL noob can do?

Thanks much,
Justin

---

### Post by Wim Sturkenboom on 2007-08-23
You need experience with (or need to learn)
[LIST=1]
[*]html (and to a lesser extent css) to be able to design forms and present data; you might be able to use tools for it (nvu, quanta)
[*]mysql to be able to create databases and tables and compose queries
[*]php to be able to connect to the database and run queries from web pages
[*]web security as you probably don't want the rest of the world to modify the data in the database
[*]apache to get php going (migt already be working because of other things that you have)
[/LIST]

Some links:
[HTML tutorial](http://www.w3schools.com/html/)
[css tutorial](http://www.w3schools.com/css/default.asp)
[Building a Database-Driven Web Site Using PHP and MySQL](http://dev.mysql.com/tech-resources/articles/ddws/index.html)
[PHP MySQL Tutorial](http://www.php-mysql-tutorial.com/)

Take small steps at a time.. Hope this helps

---

### Post by 67comet on 2007-08-23
I'll hammer out a few of these. I already admin about 10 sites via my home server so I've got Apache, MySQL, PHP, ProFTPd, Webalizer and Munin running well. I create the databases myself but one of the CMS or Wordpress handles the population for me.

I was just hoping there was an application already out there that I could plug in to what I have, set it up and hand over to the wife.

I may see if Joomla, Xoom or Wordpress can be build upon to get that going.

Thanks again :), I bookmarked the links, they are helpful no matter the need.

---

