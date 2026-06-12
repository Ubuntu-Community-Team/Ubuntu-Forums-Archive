---
title: "Apache+PHP-FPM+chroot problem &quot;File not found.&quot;"
date: 2013-04-26
forum: Server Platforms
---

### Post by Messzir on 2013-04-26
Hello everyone,

I want to set chroot to the DocumentRoot using PHP-FPM pools' chroot attribute. With the settings below, whatever I do I get only a "File not found." error:

/etc/php5/fpm/pool.d/example.conf
```
[example]
user = example
group = example
listen = /var/run/php_fpm_example.sock
pm = dynamic
pm.max_children = 5
pm.start_servers = 2
pm.min_spare_servers = 1
pm.max_spare_servers = 3
chroot = /opt/jail/example/home/example
php_admin_value[open_basedir]=/opt/jail/example/home/example
```

/etc/apache2/sites-enabled/example
```
<VirtualHost *:80>
ServerName example.domain.name
ServerAlias www.example.domain.name
DocumentRoot /opt/jail/example/home/example
<Directory /opt/jail/example/home/example>
AllowOverride All
Order Allow,Deny
Allow from all
</Directory>
<IfModule mod_fastcgi.c>
<FilesMatch \.php$>
SetHandler php-script
</FilesMatch>
Action php-script /php5-fpm-handler
Alias /php5-fpm-handler /vhost_example
FastCGIExternalServer /vhost_example -socket /var/run/php_fpm_example.sock
</IfModule>
</VirtualHost>

```


So the website itself is located in /opt/jail/example/home/example. You may find it strange, but doesn't really matter, it is caused by jailkit.

Thanks for your help.

---

### Post by Messzir on 2013-04-28
It is really important. If you can answer, please do. Thanks.

---

