---
title: "Php Error"
date: 2006-05-31
forum: Server Platforms
---

### Post by wizzkid on 2006-05-31
I installed php5 and apache2,

PHP
php5, php5-cgi, php5-cli, php5-common, php5-mysql, php5-mysqli, php-pear
APACHE
apache2, apache-common apache2-mpm-prefork, apache2-utils, lilapache2-mod-php5

Then, documentindex and add index.php.. however, when i browse php files I encounter this issue. see this snapshot [http://www.leeph.net/logs/nophp.png](http://www.leeph.net/logs/nophp.png)

Also, I enounter this error "apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName" when I start apache2. i know where i can configure this on the old apache, its just in the httpd.conf, but in apache2, i was confused.

Hope you could help.. thanks.

PS - I am using Dapper flight 7

---

### Post by harisund on 2006-05-31
wizzkid I am unable to do it right, but do try to search the forums for the same problem. If you wish, search in the forums for posts made by me 'harisund' and containing the search terms 'apache' and 'php' and look for posts. I have explained in detail what to do in other posts here.. catch you later...

---

### Post by wizzkid on 2006-05-31
Hi! Thanks a lot.. I found this site [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP) I hope this will help :D

---

### Post by Paul Bramscher on 2006-06-09
I didn't find an anwser to this problem in the sources mentioned above.

However:
I found that by adding "localhost.localdomain" to your /etc/hosts in the line with 127.0.0.1 and restarting apache, the problem went away.  It seems to want a stub domain.

---

