---
title: "Apache rewrite mod"
date: 2007-03-17
forum: Server Platforms
---

### Post by mathieumaes on 2007-03-17
I'm using Ubuntu 6.06 and I installed the default package of apache2. I need to use rewrite rules, so I have to enable the rewrite mod but it's not working.

I enabled the mod using a2enmod. If I try this again it says it's already enabled, so I think it's working.

Next, I've put a .htaccess file inside my www dir which has following content: 
<IfModule mod_rewrite.c>
Options +FollowSymlinks
 RewriteEngine on
RewriteRule ^(.*)\.html$ /index.php?page=$1 [QSA] [nc]
</IfModule>


This works on other servers, but on my Ubuntu it just seems to ignore the rewrite... What am I doing wrong ??

---

### Post by nolodude on 2007-03-26
You probably have allow override disabled in your /etc/apache2/sites-available/default file.

---

