---
title: "Apache Blank page"
date: 2011-12-19
forum: Server Platforms
---

### Post by primaverto on 2011-12-19
Hello ,


I have installed ubuntu 10.10 and apache2 and mysql


I have download one 'ban system' and when try to access admin panel blank page :(
 
Apache Error log : 
[PHP][Mon Dec 19 19:00:10 2011] [error] [client 127.0.0.1] PHP Notice:  A session had already been started - ignoring session_start() in /var/www/Web/include/access.inc.php on line 23, referer: http://localhost/Web/ban_list.php
[Mon Dec 19 19:00:10 2011] [error] [client 127.0.0.1] PHP Notice:  A session had already been started - ignoring session_start() in /var/www/Web/include/admin/admin_so_in.php on line 2, referer: http://localhost/Web/ban_list.php
[Mon Dec 19 19:00:12 2011] [error] [client 127.0.0.1] PHP Notice:  A session had already been started - ignoring session_start() in /var/www/Web/include/access.inc.php on line 23, referer: http://localhost/Web/ban_list.php
[Mon Dec 19 19:00:12 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined variable: page in /var/www/Web/ban_list.php on line 58, referer: http://localhost/Web/ban_list.php
[Mon Dec 19 19:00:12 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined variable: title2 in /var/www/Web/ban_list.php on line 203, referer: http://localhost/Web/ban_list.php
[Mon Dec 19 19:00:12 2011] [error] [client 127.0.0.1] File does not exist: /var/www/images, referer: http://localhost/Web/templates/default/css/paginator.css[/PHP]

---

