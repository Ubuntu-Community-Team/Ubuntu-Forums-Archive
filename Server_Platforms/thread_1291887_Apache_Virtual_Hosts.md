---
title: "Apache Virtual Hosts"
date: 2009-10-15
forum: Server Platforms
---

### Post by markbusu on 2009-10-15
Hi Guys,

I have two domains used on my site..

domain.com
[www.domain.com](www.domain.com)

I have a certificate file each domain. I have created two virtual hosts as follows in the default apache conf sites-available/default:

```
<VirtualHost *:443>
        ServerAdmin webmaster@localhost
        ServerName domain.com
        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride All
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride All
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride All
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

        SSLEngine on
        SSLCertificateFile /etc/ssl/certs/domain.com.crt
        SSLCertificateKeyFile /etc/ssl/private/domain.com.key

</VirtualHost>

<VirtualHost *:443>
        ServerAdmin webmaster@localhost
        ServerName www.domain.com
        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride All
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride All
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride All
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

        SSLEngine on
        SSLCertificateFile /etc/ssl/certs/www.domain.com.crt
   SSLCertificateKeyFile /etc/ssl/private/www.domain.com.key

</VirtualHost>

```

What happens is only the 1st virtual host at the top of the configuration works correctly. The second virtual host is being ignored and the certificate does not work correctly.

Is this the right way to set up two virtual hosts?

Thanks!

---

### Post by t3r0 on 2009-10-15
Hi,

Namebased virtual hosting with ssl is a no go.. you need two IPs for that setup to work..

But is there a reason why to use two virtual hosts/certs? Most of the Certificate Authorities sing the certs by default to domain.com and [www.domain.com?](www.domain.com?) 



- Tero

---

### Post by rnodal on 2009-10-15
Am I missing something?

How is domain.com and [www.domain.com](www.domain.com) different domains? 
www is just a subdomain. domain.com is the domain, unless you 
intended to type exmple.com, [www.otherdomain.com](www.otherdomain.com).

-r

---

### Post by rnodal on 2009-10-15
> **t3r0 said:**
> Hi,

But is there a reason why to use two virtual hosts/certs? Most of the Certificate Authorities sing the certs by default to domain.com and [www.domain.com?](www.domain.com?) 



- Tero

I don't think so. I think you have to buy two separate certificates. I don't see why you would want to do that when you can just buy it for [www.domain.com](www.domain.com) and redirect(mod_rewrite) the user to [www.domain.com](www.domain.com) when they access the site via domain.com. I just don't think it is cost effective but that is just my opinion.

-r

---

