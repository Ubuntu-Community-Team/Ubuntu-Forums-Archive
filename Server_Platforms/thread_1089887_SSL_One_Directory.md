---
title: "SSL One Directory"
date: 2009-03-07
forum: Server Platforms
---

### Post by rage9 on 2009-03-07
I'm trying to set up apache so that only certain directories can be accessed by https, mainly my myPHPAdmin directory.  All other attempts at https I would like directed back to the http variation. 

Any ideas?

---

### Post by hictio on 2009-03-07
Try this:

```

Alias /phpMyAdmin "/var/www/html/phpMyAdmin-2.9.2-all-languages-utf-8-only"
<Directory "/var/www/html/phpMyAdmin-2.9.2-all-languages-utf-8-only">
        SSLRequireSSL
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order deny,allow
        Deny from all

        ## Localhost
        Allow from 127.0.0.1

        ## My LAN
        Allow from 10.120.12.0/28

        AddType application/x-httpd-php .php
        php_flag magic_quotes_gpc on
        php_flag track_vars on
</Directory>

```

Of course, for this to properly work, you must have already setup SSL on the box, and also, I have another entry that blocks access to "http://www.whatever.something/phpMyAdmin-2.9.2-all-languages-utf-8-only/" so the only access is thru the alias, with SSL.

---

### Post by rage9 on 2009-03-08
Played around with it for a while, but it seems like the whole domain will also have a https counterpart, not that it's a bad thing per se.

Maybe could use some crazy url rewrites to only allow [https://domain.tld/phpmyadmin](https://domain.tld/phpmyadmin) ?  Seems like it's more work than its worth.  Anyone have any other ideas for securing phpmyadmin? 

What I'm thinking is just get another domain, and just use that purely for phpmyadmin, would be a fairly easy, cheap ordeal.

---

### Post by hictio on 2009-03-08
> **rage9 said:**
> Played around with it for a while, but it seems like the whole domain will also have a https counterpart, not that it's a bad thing per se.


Sorry, I don't understand what you mean.
The example above will force any connection to 'http://xxxxx/phpMyAdmin/' to be thru HTTPS; if you try to access the site w/o SSL, it will give you a 'Access Denied' error.

---

### Post by rage9 on 2009-03-08
What I mean is that you have to use the **SSLEngine on** command inside the VirutalHost, which is the whole domain.

Yes the PHPAdmin will be forced SSL but at the same time you can type [https://mydomain.tld](https://mydomain.tld) because now the whole domain can access the secure version which I don't want, because I'll be using a self signed certificate.

---

### Post by rage9 on 2009-03-08
For example this is basically what the VirtualHost entry looks like:

```
<VirtualHost *:80>
ServerName domain.tld
DocumentRoot /some/directory

SSLEngine on
SSLCertificateFile    /etc/ssl/certs/ssl-cert-snakeoil.pem

<Directory “/some/directory">
	Options Indexes FollowSymLinks +Includes
	AllowOverride None
</Directory>

<Directory "/usr/share/phpmyadmin">
 	SSLRequireSSL
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order deny,allow
        Deny from all
<Directory>

</VirtualHost>
```

SSL is available for the whole domain.

---

### Post by hictio on 2009-03-08
> **rage9 said:**
> What I mean is that you have to use the **SSLEngine on** command inside the VirutalHost, which is the whole domain.

Yes the PHPAdmin will be forced SSL but at the same time you can type [https://mydomain.tld](https://mydomain.tld) because now the whole domain can access the secure version which I don't want, because I'll be using a self signed certificate.

Ok, I see it now, you didn't mention this was for a virtual domain, I have used it but not that way, but as a plain vanilla alias.

---

