---
title: "apache2 virtual hosts on 11.04"
date: 2011-08-02
forum: Server Platforms
---

### Post by gypsumwolf on 2011-08-02
**Problem:** Both domains point to the same site.

**Info:**
I have a server behind a router. I have a domain.com and a sandbox.domain.com.

I have a /var/www/domain **and** /var/www/sandbox.

I have a /etc/apache2/sites-available/sandbox
I have a /etc/apache2/sites-available/domain.com

I also have a symlink /etc/apache2/sites-enabled/sandbox
I also have a symlink /etc/apache2/sites-enabled/domain.com

more httpd.conf:
```

ServerName localhost

```

more ports.config
```

# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

```

more etc/apache2/sites-available/sandbox:
```

<VirtualHost *:80>
        ServerAdmin email@email.com
        ServerName sandbox.domain.com

        DocumentRoot /var/www/sandbox
        <Directory /var/www/sandbox>
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/sandbox>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

more etc/apache2/sites-available/domain.com:
```

<VirtualHost *:80>
        ServerAdmin email@email.com
        ServerName domain.com
        ServerAlias www.domain.com

        DocumentRoot /var/www/domain.com
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

The hosts file of the desktop on the same internal network as the server:
```

127.0.0.1       localhost
127.0.1.1       someplace
10.0.0.3        domain.com
10.0.0.3        www.domain.com
10.0.0.3        mail.domain.com
10.0.0.3        sandbox.domain.com

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

---

### Post by Romu on 2011-08-03
Hi,
I would say your domain.com directory in the Apache config should be set to /var/www/domain instead of /var/www, don't you think ?

I make all my virtual hosts config by reading this doc:
[http://doc.ubuntu-fr.org/tutoriel/virtualhosts_avec_apache2]("http://doc.ubuntu-fr.org/tutoriel/virtualhosts_avec_apache2")

It is in French, sorry, but I think it's pretty readable by anyone, it's clear, and it has always worked for me. Just read the chapter 2 which is, in English, "Virtual hosts based on names".

---

### Post by gypsumwolf on 2011-08-03
Dome issue still happening.

more etc/apache2/sites-available/domain.com:
```

<VirtualHost *:80>
        ServerAdmin email@email.com
        ServerName domain.com
        ServerAlias www.domain.com

        DocumentRoot /var/www/domain.com
        <Directory /var/www/domain.com>
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/domain.com>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

---

### Post by gypsumwolf on 2011-08-03
Ok, I fixed it, but I do not know why.

In the apache2 sandbox config I added "ServerAlias sandbox.domain.com" and now it works perfect. I don't know why just "ServerName sandbox.domain.com" did not work by itself.

---

### Post by sparklypenguin on 2011-08-04
I'm having the same problem and am about at my wits end

my set up is as above with the only exception being the in the hosts.conf file i have my localhost and sites all at 127.0.0.1 
also i had already set up the ServerAlas and ServerName for both sites - so no go there

everything works fine in the local network entering mysite1.com and mysite2.com both display the correct websites but outside on the web i get directed to mysite1 regardless of which site i request.

originally it took me to the default apache2 index.html, but i removed the link within sites enabled and then was redirected to mysite1.com

its as if i'm missing a setting somewhere which allows more than one VirtualHost...?

my dyndns forwarding works fine - i use to have a xampp server running on the same box but recently changed to Ubuntu 11.04 and was loving it till i hit the wall with these VirtualHosts

so many people have the same problem it seems - but there has been no solution that works for me.... 

any help gratefully received

---

