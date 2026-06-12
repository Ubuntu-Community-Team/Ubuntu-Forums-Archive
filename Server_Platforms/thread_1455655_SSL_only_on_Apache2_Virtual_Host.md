---
title: "SSL only on Apache2 Virtual Host"
date: 2010-04-16
forum: Server Platforms
---

### Post by cian1500ww on 2010-04-16
Hi,
I currently have a virtual host setup to accept SSL connections as follows:
```

<VirtualHost *:443>
DocumentRoot "/var/www"
SSLEngine on
SSLCertificateFile /etc/apache2/ssl/apache.pem
<Directory "/var/www">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

```
How would I change it so that it can only be accessed via HTTPS ??

Thanks !!

---

### Post by cdenley on 2010-04-16
I believe with "SSLEngine on" that vhost can only be accessed with SSL encryption. If you want to make sure, you can always add this line:

```

<VirtualHost *:443>
DocumentRoot "/var/www"
SSLEngine on
SSLCertificateFile /etc/apache2/ssl/apache.pem
<Directory "/var/www">
**SSLRequireSSL**
allow from all
Options +Indexes
</Directory>
</VirtualHost>

```

---

### Post by cian1500ww on 2010-04-16
> **cdenley said:**
> I believe with "SSLEngine on" that vhost can only be accessed with SSL encryption. If you want to make sure, you can always add this line:

```

<VirtualHost *:443>
DocumentRoot "/var/www"
SSLEngine on
SSLCertificateFile /etc/apache2/ssl/apache.pem
<Directory "/var/www">
**SSLRequireSSL**
allow from all
Options +Indexes
</Directory>
</VirtualHost>

```
No luck, I think it might be because my default server's web directory is the same as the virtual host's.

---

### Post by cdenley on 2010-04-17
> **cian1500ww said:**
> No luck, I think it might be because my default server's web directory is the same as the virtual host's.

Well then they're accessing a different vhost, aren't they. You asked how a single vhost can be restricted to SSL. If you don't want to allow non-ssl connections, don't enable non-ssl vhosts. You can even disable port 80 in /etc/apache2/ports.conf.

---

### Post by dudumomo on 2010-04-17
What I do is to redirect non SSL access to SSL;

```
<IfModule mod_ssl.c> 
<VirtualHost *:80> 
        ServerName webmail.freelydifferent.com 
        Redirect / https://webmail.freelydifferent.com 
</VirtualHost> 
 
<VirtualHost _default_:443> 
        ServerAdmin spam_me@freelydifferent.com 
        ServerName webmail.freelydifferent.com 
        ServerAlias webmail.freelydifferent.com 
 
        DocumentRoot /var/www/webmail 
        <Directory /> 
                Options FollowSymLinks 
                AllowOverride None 
        </Directory> 
        <Directory /var/www/webmail> 
                Options Indexes FollowSymLinks MultiViews 
                AllowOverride None 
                Order allow,deny 
                allow from all 
        </Directory> 
etc...
```

---

