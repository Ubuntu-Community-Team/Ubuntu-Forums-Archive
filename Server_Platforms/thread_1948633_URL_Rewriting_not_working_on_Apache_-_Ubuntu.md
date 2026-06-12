---
title: "URL Rewriting not working on Apache - Ubuntu"
date: 2012-03-28
forum: Server Platforms
---

### Post by 1cookie on 2012-03-28
hi

As above I'm having problems with URL Re-writing, PHP, Apache. For example this rule:

```

RewriteRule ^shop/([A-Za-z\+]+)/?$ shop.php?type=$1

```and a URLs 

```

localhost/shop/this
localhost/shop/that

```should be loading different views based on a type= flag passed to my shop.php controller; but isn't working. It's an Apache setup thing. It ain't the script - as this works fine in windows on WAMP.



I've taken, checked the following (on my Ubuntu box) steps:

1. mod_rewrite is enabled in PHP - php.ini
2. in /etc/apache2/apache2.conf 

```

<Files ~ "^\.ht">
   Order allow,deny
   allow from all
   Satisfy all
</Files>


<Directory />
    Options FollowSymLinks
    AllowOverride All
   Order deny,allow
   Allow from all
</Directory>


```so .htaccess is switched on.


Have I overlooked anything??

---

### Post by uRock on 2012-03-28
Moved to *Server Platforms*

---

### Post by 1cookie on 2012-03-30
Entering something like this does the trick:

```

<Directory /path/to/specific/directory >     
Options FollowSymLinks    
 AllowOverride All    
Order deny,allow    
Allow from all 
</Directory>

```

---

