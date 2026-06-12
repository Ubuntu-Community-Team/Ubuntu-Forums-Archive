---
title: "Getting phpMyAdmin to recognize (and import to) a virtual host/domain"
date: 2011-11-17
forum: Server Platforms
---

### Post by CoolBreeze47 on 2011-11-17
Hi everyone

I have a LAMP server set up on Ubuntu 11.10 along with a copy of phpMyAdmin. PhpMyAdmin is in the main folder and can be accessed using: localhost/phpMyAdmin. I have 3 virtual domains as well which can be accessed by...

localhost/folder1
localhost/folder2
localhost/folder3

PhpMyAdmin works just fine. I can display it in the browser, login using the MySQL password I created and even create databases/import, etc.

The first domain (ie; localhost/folder1) is a PHP/MySQL driven site. The other two are static HTML pages. What I am having a lot of difficulty with is linking/associating phpMyAdmin with localhost/folder1 so that when I import an SQL dump, it will populate "folder1" with the data. When I tried this earlier and went to localhost/folder1, I received a message that the site "could not connect to the database".

Could someone please tell me step-by-step and in reasonably simple terms how I can get phpMyAdmin to recognize folder1 and understand that this site is where I want the SQL database imported to?.

Thanks in advance for any help on this (I've been racking my brains over this all day).

- CB

---

### Post by SeijiSensei on 2011-11-18
phpMyAdmin only manages the database; it's entirely independent from any applications that use the database.  You need the appropriate code in your application to connect to the database and manipulate the data.  If you're using PHP, you'll find help [here](http://php.net/manual/en/book.mysql.php).

What kinds of errors do you see in /var/log/apache2/error.log when you try to run the application?

---

