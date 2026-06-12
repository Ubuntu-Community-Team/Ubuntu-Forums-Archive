---
title: "Several config issues apache2 and phpmyadmin"
date: 2006-06-04
forum: Server Platforms
---

### Post by rickmans on 2006-06-04
I just performed an install for a development server with the following (i hope wellknown ;)) command:
```
sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql
```

after I completed the installation I changed /etc/apache2/sites-available/default  and updated the document root with the directory I preferred to be the document root and also updated the Directory with the preferred document root instead of /var/www/. 

Besides the updates of the files I added a new user to mysql and removed the logins for root.

So far everything works fine and the local sites are visitable, allthough I have got a few issues left:
* is seems that .htaccess file that is in the new document root is ignored, which options should I adjust to ensure apache will use this file?
* I would like to use the option that pma has to bookmark queries (and all other pma specific functionalities). How should I enable that?

---

### Post by rickmans on 2006-06-04
Something to add, this is the content of my .htaccess:
```
<IfModule mod_rewrite.c>
  RewriteEngine On
  RewriteBase /
  
  RewriteCond %{REQUEST_FILENAME} -f [OR]
  RewriteCond %{REQUEST_FILENAME} -d
  RewriteRule ^.*$ - [S=41]
  
  RewriteRule   (.*)  index.php
</IfModule>
```

Could it be the mod_rewrite module is not compiled by default?

---

### Post by rickmans on 2006-06-04
Okay, I solved 1 of the issues concerning the mod rewrite.

To enable the module:
sudo ln -s /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled/

sudo gedit /etc/apache2/sites-enabled/000-default

adjust:
allowOverride none in allowOverride all

---

