---
title: "php on lamp"
date: 2012-10-11
forum: Server Platforms
---

### Post by diski on 2012-10-11
Hi everybody
I installed LAMP on my ubuntu server..and I put a test html page in /var/www and everything is working ok when i log to the site from the internet..the problem is,yesterday I tried to write a php code in the html body but it didnt run?


Thanks u
Martin

---

### Post by Tralce on 2012-10-11
You need to edit your /etc/apache2/mods-enabled/php5.conf. This file tells Apache what types of files to pass to PHP. You may notice that .html is missing. Make sure your conf looks like this:
```
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3 .html
  AddType application/x-httpd-php-source .phps
</IfModule>

```
Notice how I've added .html there. 

Oh, and don't forget to "apache2ctl restart" after you do that edit.

---

