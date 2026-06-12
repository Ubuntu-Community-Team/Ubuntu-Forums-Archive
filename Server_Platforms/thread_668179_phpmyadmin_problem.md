---
title: "phpmyadmin problem"
date: 2008-01-15
forum: Server Platforms
---

### Post by honiball on 2008-01-15
I have installed phpMyAdmin on my Ubuntu 6.06. Everything seemed to go OK until I tried to access the website. I go the following errors along with the expected website:


Warning: preg_match: internal pcre_fullinfo() error -3 in /usr/local/apache2/htdocs/phpMyAdmin-2.11.4-english/libraries/core.lib.php on line 356

Warning: Cannot modify header information - headers already sent by (output started at /usr/local/apache2/htdocs/phpMyAdmin-2.11.4-english/libraries/core.lib.php:356) in /usr/local/apache2/htdocs/phpMyAdmin-2.11.4-english/libraries/auth/cookie.auth.lib.php on line 109


The file I downloaded and installed is: phpMyAdmin-2.11.4-english.tar.gz
My Apache2 webserver is serving files from: /usr/local/apache2/htdocs
I installed phpmyadmin to that location.

Any ideas?

Thanks.

Andrew

---

### Post by honiball on 2008-01-15
I have partly solved my own problem;  I changed the authentication from cookies to http in config.inc.php  (is this a bad idea?).

I can now log in and navigate around in phpmyadmin, but I get error messages like the one below when I select a database:

-------------------------------------
Warning: preg_match: internal pcre_fullinfo() error -3 in /usr/local/apache2/htdocs/phpMyAdmin-2.11.4-english/db_structure.php on line 259

Warning: preg_match: internal pcre_fullinfo() error -3 in /usr/local/apache2/htdocs/phpMyAdmin-2.11.4-english/db_structure.php on line 280
------------------------------------------

Any ideas on what is wrong and how to fix it?

---

### Post by honiball on 2008-01-17
I have managed to solve the problem by editing the php.ini file as follows:
error_reporting = E_ERROR

Aparently this will only display critical errors.

Thanks.

Andrew

---

