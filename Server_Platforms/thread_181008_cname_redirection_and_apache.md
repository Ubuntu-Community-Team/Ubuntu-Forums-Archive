---
title: "cname redirection and apache"
date: 2006-05-23
forum: Server Platforms
---

### Post by brassmonkey on 2006-05-23
Hi, 

I have a apache web server on my breezy machine.  I bought a domaine name and ask my seller to make a CNAME type redirection to a dydns.org address.

I changed my apache sites-available and site-enabled files (default and 000-default...) like this :

```
NameVirtualHost *
<VirtualHost www.clubhondafitquebec.com>
        ServerAdmin webmaster@localhost
        ServerName www.clubhondafitquebec.com

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
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
```

Then, when i stop/start the server I get this message :

```
punker@festiva:~$ sudo /etc/init.d/apache2 stop
Password:
 * Stopping web server (Apache2)...      [Mon May 22 18:51:19 2006] [warn] NameVirtualHost *:0 has no VirtualHosts
[ ok ]
```

My domain name seller tells me that the CNAME redirection is ok :

```
@     NS   ns1.domainpeople.com  
   @     NS   ns2.domainpeople.com  
   @     MX 10   mail2.domainpeople.com  
   www CNAME   brassmonkey.homedns.org  
   @     CNAME   brassmonkey.homedns.org  
    www2 A   204.174.223.28 

```

If I go to my domaine, it still don't work...  but brassmonkey.homedns.org works...

any idea ?

is the apache server can handle CNAME redirection by default ?

thanks you :)

---

