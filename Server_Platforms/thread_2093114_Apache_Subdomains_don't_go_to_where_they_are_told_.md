---
title: "Apache Subdomains don't go to where they are told to go"
date: 2012-12-09
forum: Server Platforms
---

### Post by Master_Taco on 2012-12-09
I am using Ubuntu 12.04, and Webmin to set up a web server. The server works just dandy if I create a virtual host and point my domain to the server. I can go to my site just fine by going to domain.com or [www.domain.com]("http://www.domain.com"). What doesn't work, is subdomains. 

I created a new Virtual Host in Webmin to point to subdomain.domain.com on port 80. My DNS zones are set up so subdomain.domain.com points to my IP address, but when I go to subdomain.domain.com, it loads up the site that domain.com (no subdomain) is supposed to be going to, despite the fact that subdomain.domain.com is supposed to be pointing to /home/subdomain/www (existing directory) and domain.com points to /var/www.

What in the bloody hell am I doing wrong? This is extremely frustrating, because from past experience, I should be done right now. I've done this before on a past version of Ubuntu with Webmin...

I am extremely tired and frustrated, so I'm sure I've missed something, so if you need more information, just let me know I'll cough it up.

---

### Post by pkadeel on 2012-12-10
> **Master_Taco said:**
> I am using Ubuntu 12.04, and Webmin to set up a web server. The server works just dandy if I create a virtual host and point my domain to the server. I can go to my site just fine by going to domain.com or [www.domain.com]("http://www.domain.com"). What doesn't work, is subdomains. 

I created a new Virtual Host in Webmin to point to subdomain.domain.com on port 80. My DNS zones are set up so subdomain.domain.com points to my IP address, but when I go to subdomain.domain.com, it loads up the site that domain.com (no subdomain) is supposed to be going to, despite the fact that subdomain.domain.com is supposed to be pointing to /home/subdomain/www (existing directory) and domain.com points to /var/www.

What in the bloody hell am I doing wrong? This is extremely frustrating, because from past experience, I should be done right now. I've done this before on a past version of Ubuntu with Webmin...

I am extremely tired and frustrated, so I'm sure I've missed something, so if you need more information, just let me know I'll cough it up.
make sure you have not defined an alias as *.domain.com in you main domain.com virtual host.

---

### Post by volkswagner on 2012-12-10
Please post the output of the following:

```
ls /etc/apache2/sites-enabled
```

```
cat /etc/apache2/ports.conf
```

---

### Post by Master_Taco on 2012-12-10
> **volkswagner said:**
> Please post the output of the following:

```
ls /etc/apache2/sites-enabled
``````
cat /etc/apache2/ports.conf
```

```
Mon Dec 10 09:50:58 CST 2012
~
justin@ubuntu-web-server: pts/1: 17 files b -> ls /etc/apache2/sites-enabled
webmin.1355111967.conf  webmin.1355112046.conf

```

```
Mon Dec 10 09:51:13 CST 2012
~
justin@ubuntu-web-server: pts/1: 18 files b -> cat /etc/apache2/ports.conf
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

Listen *:80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
Listen *:443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

```

---

### Post by volkswagner on 2012-12-10
I really don't like how Webmin handles virtualhosts.  You will be having more joy by avoiding webmin to administer apache2.

With that said lets see if we can get it working.

What do the vhost files look like?

```
cat /etc/apache2/sites-available/webmin.1355111967.conf
```

```
cat /etc/apache2/sites-available/webmin.1355112046.conf
```

Normally port.conf should included the NamedVirtualHost directive, but I have a suspicion webmin adds it to each vhost file.

ports.conf should have:

```
NameVirtualHost *:80
```

The above should match your vhost file opening tag either *, *:80, or even your ip instead of *, anyway the portion after host needs to match.

```
<VirtualHost *:80>
```

---

### Post by Master_Taco on 2012-12-10
> **volkswagner said:**
> I really don't like how Webmin handles virtualhosts.  You will be having more joy by avoiding webmin to administer apache2.

With that said lets see if we can get it working.

What do the vhost files look like?

```
cat /etc/apache2/sites-available/webmin.1355111967.conf
``````
cat /etc/apache2/sites-available/webmin.1355112046.conf
```Normally port.conf should included the NamedVirtualHost directive, but I have a suspicion webmin adds it to each vhost file.

ports.conf should have:

```
NameVirtualHost *:80
```The above should match your vhost file opening tag either *, *:80, or even your ip instead of *, anyway the portion after host needs to match.

```
<VirtualHost *:80>
```


```
Mon Dec 10 09:52:15 CST 2012
~
justin@ubuntu-web-server: pts/1: 18 files b -> cat /etc/apache2/sites-available/webmin.1355111967.conf
<VirtualHost _default_:80>
DocumentRoot /var/www
<Directory "/var/www">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

``````
Mon Dec 10 19:55:24 CST 2012
~
justin@ubuntu-web-server: pts/1: 18 files b -> cat /etc/apache2/sites-available/webmin.1355112046.conf
<VirtualHost kyle.thecdrive.com:80>
DocumentRoot /home/kyle/www
<Directory "/home/kyle/www">
allow from all
Options +Indexes
</Directory>
ServerName kyle.thecdrive.com
</VirtualHost>


```

Looks to me like everything is peachy. :\

---

### Post by volkswagner on 2012-12-11
I would add the following directive to ports.conf.

```
NameVirtualHost *:80
```

Then restart apache2.

---

### Post by koenn on 2012-12-11
you need
```

<VirtualHost *>
    ServerName kyle.thecdrive.com

# + the rest : directory def, etc.
</VirtualHost>

```

It's the ServerName directive that lets apache distinguish between name based vhosts. Without it, a vhost def defaults to the "main" server. 



[http://httpd.apache.org/docs/2.2/mod/core.html#virtualhost](http://httpd.apache.org/docs/2.2/mod/core.html#virtualhost)




and, of course, restart or reload after config changes, as always.

---

### Post by Master_Taco on 2012-12-11
> **koenn said:**
> you need
```

<VirtualHost *>
    ServerName kyle.thecdrive.com

# + the rest : directory def, etc.
</VirtualHost>

```It's the ServerName directive that lets apache distinguish between name based vhosts. Without it, a vhost def defaults to the "main" server. 



[http://httpd.apache.org/docs/2.2/mod/core.html#virtualhost](http://httpd.apache.org/docs/2.2/mod/core.html#virtualhost)




and, of course, restart or reload after config changes, as always.

I don't think I'm understanding what you're trying to say, because to me you're telling me to add the ServerName directive to the kyle.thecdrive.com's vhost, but that already exists. I looked at the link you gave me, and it appears to be set up correctly, the only things it's missing is the Logs and ServerAdmin directives, which as far as I'm aware are non-critical to the functioning of the server, right?

---

### Post by Master_Taco on 2012-12-11
> **volkswagner said:**
> I would add the following directive to ports.conf.

```
NameVirtualHost *:80
```Then restart apache2.
Unfortunately, adding that did not do anything at all. :( I added it under the line "Listen", like this: 
```
Listen *:80
NameVirtualHost *:80

```

---

### Post by koenn on 2012-12-11
> **Master_Taco said:**
> I don't think I'm understanding what you're trying to say, because to me you're telling me to add the ServerName directive to the kyle.thecdrive.com's vhost, but that already exists. I looked at the link you gave me, and it appears to be set up correctly, the only things it's missing is the Logs and ServerAdmin directives, which as far as I'm aware are non-critical to the functioning of the server, right?

hm, you're right. I overlooked it in your file because it's at the bottom of the section; I expect it at the top.

Anyway, try the Virtualhost tag without a FQDN, then, like so
```
<VirtualHost *>
```
or so
```
<VirtualHost *:80>
```

what you want in that tag is an IP address (+ port), or a wildcard (any address); not a hostname.

Other than that, nothing relly jumps out. 
Maybe reboot, just to make sure ?

---

### Post by volkswagner on 2012-12-11
> **koenn said:**
> hm, you're right. I overlooked it in your file because it's at the bottom of the section; I expect it at the top.

Anyway, try the Virtualhost tag without a FQDN, then, like so
```
<VirtualHost *>
```
or so
```
<VirtualHost *:80>
```

what you want in that tag is an IP address (+ port), or a wildcard (any address); not a hostname.

Other than that, nothing relly jumps out. 
Maybe reboot, just to make sure ?

I agree with koenn.

I'm glad you tried first putting the NameVitualHost directive in ports.conf.  I was not sure if that alone would work.  As stated, I really don't like the way webmin handles config files.  I assume that webmin added the following to each of your vhost files.

```
<VirtualHost kyle.thecdrive.com:80>
```

and

```
<VirtualHost _default_:80>
```

Since you have :80 in ports.conf  I would change the above as koenn stated in each vhost file.

to:

```
<VirtualHost *:80>
```

I think this can be avoided when using webmin.  There should be a checkbox for all hosts or all requests or similar, when creating your vhost.

---

### Post by Rakeshvijayan on 2012-12-12
Hi friend I had setup sites in virtual host for two sites with out help of webmin  but dns name for two site is my problem is my problem 
[http://ubuntuforums.org/showthread.php?t=2092256](http://ubuntuforums.org/showthread.php?t=2092256)


my m.com sites virtual host files look like this 

sudo nano /etc/apache2/site-available/m.com
> <VirtualHost *:80>
    ServerAdmin [email]webmaster@m.com[/email]
    ServerName m.com
    ServerAlias [www.m.com](www.m.com)
    DocumentRoot /var/www/doc/m.com
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

MY c.com site configuration file look like this 
> <VirtualHost *:80>
    ServerAdmin [email]webmaster@c.com[/email]
    DocumentRoot /var/www/c.com
    ServerName c.com
    ServerAlias [www.c.com](www.c.com)
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

I didn't read the whole content of your question .this may help you to solve the problem ,but I am waiting for any one help .........

---

### Post by Master_Taco on 2012-12-12
> **volkswagner said:**
> I agree with koenn.

I'm glad you tried first putting the NameVitualHost directive in ports.conf.  I was not sure if that alone would work.  As stated, I really don't like the way webmin handles config files.  I assume that webmin added the following to each of your vhost files.

```
<VirtualHost kyle.thecdrive.com:80>
```and

```
<VirtualHost _default_:80>
```Since you have :80 in ports.conf  I would change the above as koenn stated in each vhost file.

to:

```
<VirtualHost *:80>
```I think this can be avoided when using webmin.  There should be a checkbox for all hosts or all requests or similar, when creating your vhost.

Changing VirtualHost to wildcard worked! However, now when I add another vhost for a different subdomain, the new subdomain works, the old subdomain works, but the main site (sans the subdomain) changes to whatever the newest subdomain's site is. The directives are exactly the same as the original subdomain, except the subdomain and the directory where files should be read from... I think something is misconfigured somewhere, but I wouldn't know where to begin looking...

---

### Post by Rakeshvijayan on 2012-12-12
Hi friend I had setup sites in virtual host for two sites with out help of webmin  but dns name for two site is my problem is my problem 
[http://ubuntuforums.org/showthread.php?t=2092256](http://ubuntuforums.org/showthread.php?t=2092256)


my m.com sites virtual host files look like this 

sudo nano /etc/apache2/site-available/m.com
> <VirtualHost *:80>
    ServerAdmin [EMAIL="webmaster@m.com"]webmaster@m.com[/EMAIL]
    ServerName m.com
    ServerAlias [www.m.com]("http://www.m.com")
    DocumentRoot /var/www/doc/m.com
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

</VirtualHost>MY c.com site configuration file look like this 
> <VirtualHost *:80>
    ServerAdmin [EMAIL="webmaster@c.com"]webmaster@c.com[/EMAIL]
    DocumentRoot /var/www/c.com
    ServerName c.com
    ServerAlias [www.c.com]("http://www.c.com")
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

</VirtualHost>After this you need to enable both site like this 
> a2ensite m.com c.com 
sudo service apache2 reload I didn't read the whole content of your question .this may help you to solve the problem ,but I am waiting for any one help .........


Thanks this may be your answer

---

### Post by Master_Taco on 2012-12-12
Okay, I think that Webmin is misconfigured somewhere because when I deleted the new vhost that it created, used the cp command to duplicate the vhost file of the original subdomain and edited that in VI. Now everything works just peachy... I have no idea what Webmin is doing, because the vhost file I created looks EXACTLY like the one that Webmin generated, so I think that Webmin is changing some other file somewhere else that is influencing Apache...

---

### Post by Rakeshvijayan on 2012-12-12
> **Master_Taco said:**
> Okay, I think that Webmin is misconfigured somewhere because when I deleted the new vhost that it created, used the cp command to duplicate the vhost file of the original subdomain and edited that in VI. Now everything works just peachy... I have no idea what Webmin is doing, because the vhost file I created looks EXACTLY like the one that Webmin generated, so I think that Webmin is changing some other file somewhere else that is influencing Apache...

please share the information that you achieved now because All new one will confuse and stuck some where .by doing so our experience lead them in correct path   


ok what you are trying to do with apache virtual host .do you make dns entry for the vhosted sites 

Thanks

---

### Post by volkswagner on 2012-12-12
> **Master_Taco said:**
> Okay, I think that Webmin is misconfigured somewhere because when I deleted the new vhost that it created, used the cp command to duplicate the vhost file of the original subdomain and edited that in VI. Now everything works just peachy... I have no idea what Webmin is doing, because the vhost file I created looks EXACTLY like the one that Webmin generated, so I think that Webmin is changing some other file somewhere else that is influencing Apache...

This is exactly why I mention "I don't like the way Webmin handles Apache2 config files".  I tried webmin a few years back.  The results from webmin can become unexpected.  I found problems grew worse when mixing hand edited files along with webmin configured files.  This may be a small part of the reason why Ubuntu dropped support for Webmin

---

### Post by SeijiSensei on 2012-12-12
Webmin was written initially to manage RedHat-flavored machines.  It works well on that platform, but everything I've read suggests its support for Debian-based distros is not up to snuff.

OP, if you really want to use Webmin, I suggest installing [CentOS 6]("http://www.centos.org/") instead of Ubuntu.  If you would prefer to stick with Ubuntu, then dump Webmin and just follow the instructions in the [Ubuntu Server Guide]("https://help.ubuntu.com/12.04/serverguide/").

---

### Post by Cheesemill on 2012-12-12
A big +1 for not using Webmin, it's caused me no end of problems in the past on Debian and Ubuntu systems by not using the standard locations and then using ugly hacks instead of best practices for its configuration files.

If you must have a WebUI for your server then I would recomend using Zentyal instead, it's been designed from the ground up for administrating Ubuntu.

[http://www.zentyal.org/](http://www.zentyal.org/)

---

