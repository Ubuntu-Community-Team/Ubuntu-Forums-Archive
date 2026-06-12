---
title: "apache with php4. php pages only allow 'save as' in FireFox"
date: 2006-01-07
forum: Server Platforms
---

### Post by andrewsawyer on 2006-01-07
I have installed apache and php4 using the following:

```
sudo apt-get install apache2
sudo apt-get install php4
sudo /etc/init.d/apache2 restart
```

However if I stick testphp.php containing 

```
<?php phpinfo(); ?>
```

Then view it in FF, I get a message asking me where I would like to save the file?!?!

I've also tried adding 

```
LoadModule php4_module
DirectoryIndex index.html index.php
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

``` into /etc/apache2/apache2.conf, however this hasn't helped either.

Can someone please tell me where I'm going wrong?  html files load fine, and I have tried this across my local network, and from outside my local network via dyndns.org.

Many thanks in advance,

Andy

---

### Post by andrewsawyer on 2006-01-09
Fixed it - had to apt-get --purge remove all apache/php stuff, then start again.  All good now.

---

