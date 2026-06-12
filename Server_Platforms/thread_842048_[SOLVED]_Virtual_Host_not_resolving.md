---
title: "[SOLVED] Virtual Host not resolving"
date: 2008-06-27
forum: Server Platforms
---

### Post by momilla on 2008-06-27
I am attempting to setup hosting for separate websites on single static IP address. I set up vhost file, and neither the main domain,(mydomain.com) or the sub domain (test.mydomain.com) is accessible via the web. It seems to not be able to resolve either. Before i enabled the vhost, mydomain.com was accessible. after enabling vhost for test.mydomain.com neither site is available. here is my vhost conf file for the sub domain. if i disable virtyual hosting, the primary domain (mydomain.com) is accessible:

 #
    # sub.domain.com (/etc/apache2/sites-available/sub.domain.com)
    #
    <VirtualHost 10.0.0.10:80>
    ServerAdmin [email]e-mail@bellsouth.net[/email]
    ServerName test.mydomain.com
    ServerAlias test.mydomain.com
    # Indexes + Directory Root.
    DirectoryIndex index.html index.htm index.php
    DocumentRoot /var/www/virtual
    # CGI Directory
    ScriptAlias /cgi-bin /var/www/virtual/cgi-bin
    <Location /cgi-bin>
    Options +ExecCGI
    </Location>

    # Logfiles
    ErrorLog /var/www/virtual/logs/error.log
    CustomLog /var/www/virtual/logs/access.log combined
    </VirtualHost>

do i need to have an internal DNS setup to point the request to the proper ip address.

I have a free DNS service that points ip traffic for my primary domain to the internal web server via my router.

any and all help is appreciated

---

### Post by windependence on 2008-06-27
The first line of your Vhost directive is restricting it to a private address;

```
<VirtualHost 10.0.0.10:80>
```

Should probably be:

```
<VirtualHost *:80>
```

-Tim

---

### Post by momilla on 2008-06-27
Thanks, that did bring my main site back, but i still have the issue of the virtual sites not working. I am going to redo all of the vhost files in sites-available, and reload them and see what happens. I will post my results

---

### Post by osjak on 2008-06-28
I believe you need to use NameVirtualHost directive as well:
```

NameVirtualHost *:80
<VirtualHost *:80>
.
.
.
</VirtualHost>

```

[http://httpd.apache.org/docs/2.2/vhosts/](http://httpd.apache.org/docs/2.2/vhosts/)

---

### Post by momilla on 2008-06-29
do i need to use the VirtualHost directive on all vhost sites or just the default site.

---

### Post by momilla on 2008-06-29
this is one of my vhost config files. when i try to access the site test.domain.com, , i get the main site, domain.com) and not the vhost site. 

NameVirtualHost *:80
<VirtualHost *:80 >
        ServerName test.domain.com
        ServerAlias test.domain.com
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/virtual
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/virtual>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /var/www/virtual/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

ScriptAlias /cgi-bin/ /var/www/virtual/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined                                 
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

---

### Post by osjak on 2008-06-29
> **momilla said:**
> do i need to use the VirtualHost directive on all vhost sites or just the default site.

Yes, you need to tell Apache about every virtual host you plan on using. The way you do it is through using the VirtualHost enclosure. Docs on Apache website are pretty well written, please read the page I posted above. Also, here's an example from Apache website on using VirtualHost enclosures to specify your hosts:

```
# Ensure that Apache listens on port 80
Listen 80

# Listen for virtual host requests on all IP addresses
NameVirtualHost *:80

<VirtualHost *:80>
DocumentRoot /www/example1
ServerName www.example.com

# Other directives here

</VirtualHost>

<VirtualHost *:80>
DocumentRoot /www/example2
ServerName www.example.org

# Other directives here

</VirtualHost>
```
[http://httpd.apache.org/docs/2.2/vhosts/examples.html](http://httpd.apache.org/docs/2.2/vhosts/examples.html)

---

### Post by theonegod on 2008-06-29
Put all your vhosts in one file and you should be able to just say it once at the top.

---

### Post by momilla on 2008-06-30
Thanks for the assist guys. once i put the vhosts in one file and commented out the listen directive in /etc/apache2/ports.conf, since i had it in the vhost file, both sites are now available.

---

