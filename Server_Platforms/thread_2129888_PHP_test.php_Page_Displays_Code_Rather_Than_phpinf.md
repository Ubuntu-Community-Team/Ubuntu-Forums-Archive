---
title: "PHP test.php Page Displays Code Rather Than phpinfo Help Please"
date: 2013-03-27
forum: Server Platforms
---

### Post by mypcnetworks on 2013-03-27
Ubuntu 12.04.2 LTS
PHP5
apache2 apache2-doc apache2-mpm-prefork apache2-utils apache2-suexec libexpat1 ssl-cert libapache2-mod-php5 libapache2-mod-ruby libapache2-mod-python php5  php5-common php5-curl php5-dev php5-gd php5-idn php-pear php5-imagick  php5-imap php5-mcrypt php5-memcache php5-ming php5-mysql php5-pspell  php5-recode php5-snmp php5-sqlite php5-suhosin php5-tidy php5-xcache  php5-xmlrpc php5-xsl

This is a fresh installation created in the last 2 days!

I have found that while getting ready to continue setting up a LAMP for internal testing, that php5 is not functioning on this server.

I have created the file *index.php *within */var/www* which contains:
```


# index.php 
<?php phpinfo(); ?>


```

After this I edited *vi /etc/apache2/apache2.conf* adding:
```

<IfModule dir_module>
DirectoryIndex index.html index.shtml index.php
</IfModule>

```

After this I restarted Apache2 *service apache2 restart*.
 But when I access the server http://<LOCAL IP>/index.php the actual php code is displayed:
```

# index.php 
<?php phpinfo(); ?>

```

Rather than phpinfo, what would be the best plan of determining why php5 installation is failied?

Thanking you in advance.

Best Regards
Pat Taylor

---

### Post by SeijiSensei on 2013-03-27
deleted

---

### Post by cariboo on 2013-03-28
Have you got php5.conf and php5.load in /etc/apache2/mods-enabled?

---

