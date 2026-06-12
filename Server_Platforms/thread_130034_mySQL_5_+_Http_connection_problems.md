---
title: "mySQL 5 + Http connection problems"
date: 2006-02-15
forum: Server Platforms
---

### Post by Wavboy on 2006-02-15
Hi
I'm quite new to ubuntu, for a project I'm working on I needed mySQL 5. After a lot of effort I got it installed, well nearly.

I can connect to mySQL through Putty.

I can connect to mySQL though phpmyadmin.

But I can't get a connection through http. I keep getting this message

Warning: mysql_connect() [function.mysql-connect]: Lost connection to MySQL server during query in /var/www/apache2-default/Shorten.php on line 3

Also PHP show's my SQL version as Client API version 4.0.24

Can anyone help?

---

### Post by siefkencp on 2006-02-16
Can you post the PHP your using to make the connection?

Since phpMyAdmin runs ok, the connection is actually being made from PHP (it's not really an http) all we need to do is get your code talking to the server correctly.

---

