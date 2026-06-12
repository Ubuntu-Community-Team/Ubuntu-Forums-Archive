---
title: "Apache2 virtual hosts foreign characters"
date: 2010-04-23
forum: Server Platforms
---

### Post by Creek on 2010-04-23
Hello!

I've run into some problems when I'm trying to add a virtual host with a foreign character in the domain name.
The foreign character is **ö**.

I've read earlier threads where it was said I should puny code it, which then translates to **xn--nda**

I then created a virtual host, as shown (replaced the real domain with *examplö*:
```

<VirtualHost *:80>    
    ServerAdmin me@examplö.com
    ServerName examplö.com
    ServerAlias examplxn-nda.com
    
    DocumentRoot /var/www/examplo
    <Directory /var/www/examplo>
        Options Indexes FollowSymLinks
        AllowOverride All 
        Order allow,deny
        allow from all
    </Directory>

    ErrorLog /var/log/apache2/examplo_error.log
    LogLevel warn
    CustomLog /var/log/apache2/examplo_access.log combined

</VirtualHost>

```

However, apache2 doesn't recognize this when I try to enter the domain, it just shows my 000default.

Any help is appreciated!

---

### Post by cdenley on 2010-04-23
Punycode is not simple substition.

ö = xn--nda
examplö.com != examplxn-nda.com
examplö.com = xn--exampl-1xa.com

[http://mct.verisign-grs.com/](http://mct.verisign-grs.com/)
[http://en.wikipedia.org/wiki/Punycode#Encoding_procedure](http://en.wikipedia.org/wiki/Punycode#Encoding_procedure)

---

### Post by Creek on 2010-04-24
Thanks, that cleared things up.

Anyway, what I read earlier was wrong too.
The ServerName should contain the punycoded string, while the alias is the regular one.

```

<VirtualHost *:80>    
    ServerAdmin me@examplö.com
    ServerName xn--exampl-1xa.com
    ServerAlias examplö.com
    
    DocumentRoot /var/www/examplo
    <Directory /var/www/examplo>
        Options Indexes FollowSymLinks
        AllowOverride All 
        Order allow,deny
        allow from all
    </Directory>

    ErrorLog /var/log/apache2/examplo_error.log
    LogLevel warn
    CustomLog /var/log/apache2/examplo_access.log combined
</VirtualHost>

```

---

