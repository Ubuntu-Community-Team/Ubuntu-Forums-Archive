---
title: "Cannot access my other virtual hosts on ubuntu server"
date: 2011-05-19
forum: Server Platforms
---

### Post by Logansanoh on 2011-05-19
Hi all, first time poster, but please help. I have been searching and reconfiguring for 6 days now and have lost several clumps of hair..

PROBLEM:
I want 2+ virtual hosts on my ubuntu server (1 ip)
BUT - Only the first "alphabetically" listed sites-enabled shows.
000-default
[www.domain1.com](www.domain1.com)
[www.domain2.com](www.domain2.com)

Individually they all work (if i a2dissite for each leaving 1)

CONFIG:
UBUNTU 10.10 Server
EC2 instance (dont shoot me for this part - hoping this isnt the issue!)
APACHE 2.2.16
DNS my.domain.com
 - to my public ec2 dns (this works)

Virtual Hosts:
# default

```
<VirtualHost *:80>
        DocumentRoot "/home/www/"
        <Directory />
        Options FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Satisfy all
        </Directory>
        <Directory /home/www>
        Options Indexes Multiviews FollowSymLinks
        AllowOverride all
        Order allow,deny
        Allow from all
        </Directory>
        LogLevel debug
        ErrorLog /home/www/logs/error.log
        CustomLog /home/www/logs/access.log "combined"
</VirtualHost>

```

Virtual Host 1 - domain1

```
<VirtualHost *:80>
        ServerAdmin webmaster@domain1.com
        ServerName domain1.com
        ServerAlias domain1.com
        ServerAlias www.domain1.com
        # Indexes + Directory Root.
        DirectoryIndex index.php
        DocumentRoot "/home/www/www.domain1.com/"
        # Directory directive
        <Directory "/home/www/www.domain1.com">
                Options Indexes Multiviews FollowSymLinks
                AllowOverride none
                Order allow,deny
                Allow from all
        </Directory>
        # CGI Directory
        ScriptAlias /cgi-bin/ /home/www/www.domain1.com/cgi-bin
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>
        # Logfiles
        LogLevel debug
        ErrorLog "/home/www/www.domain1.com/logs/error.log"
        CustomLog "/home/www/www.domain1.com/logs/access.log" combined
</VirtualHost>

```

I also have the above for domain2 in another document root with a different domain name

sym links are in place:
my apache2ctl -St shows the following - 
VirtualHost configuration:
*:80       is a NameVirtualHost
         default server  (/etc/apache2/sites-enabled/000-default:4)
         port 80 namevhost  (/etc/apache2/sites-enabled/000-default:4)
         port 80 namevhost domain1.com (/etc/apache2/sites-enabled/www.domain1.com:4)
         port 80 namevhost [www.domain2.com](www.domain2.com) (/etc/apache2/sites-enabled/www.domain2.com:4)
Syntax OK

My ports.conf:
NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    NameVirtualHost *.443
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

No changes from default to my apache2.conf and httpd.conf is empty.

I have tried the following (and about a hundred others):

[]("http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/")
[http://httpd.apache.org/docs/2.2/rewrite/vhosts.html]("http://httpd.apache.org/docs/2.2/rewrite/vhosts.html")
[http://ubuntuforums.org/archive/index.php/t-1466665.html]("http://ubuntuforums.org/archive/index.php/t-1466665.html")
[http://flurdy.com/docs/ec2/basics/index.html]("http://flurdy.com/docs/ec2/basics/index.html")
[http://www.webmasterworld.com/apache/3282118.htm]("http://www.webmasterworld.com/apache/3282118.htm")

 it seems i have tried everything that everyone else is having issues with but nothing seems to fix mine.

Possibilities:
1) EC2
2) Permissions on the files - I changed everything to the apache2 user "www-data" - no dice.
3) I am a dope...lets hope its that and one of you kind people point me to my issue. :)

Chat soon...ill be over here losing my hair.
Regards, Logansanoh

---

### Post by volkswagner on 2011-05-19
Only two things stand out for me.

You don't want two lines for ServerAlias.  Use space separated list.

```
ServerAlias www.domain1.com domain2.com www.domain2.com
```

You also don't have a server name listed in the default.  What are you trying to accomplish with the default?

Do you have any .htaccess or rewrite conditions added?

---

### Post by Logansanoh on 2011-05-19
Hey, thanks for the reply.
Made the changes to the aliases. No dice.

I do have a .htaccess in the domain1 sub dir:
```
<IfModule mod_php4.c>
    php_value session.use_trans_sid 0
</IfModule>
<IfModule mod_security.c>
SecFilterEngine Off
SecFilterScanPOST Off
</IfModule>
RewriteEngine On
#RewriteBase /sNews17
RewriteCond %{REQUEST_FILENAME} -f
RewriteRule ^(.*) $1 [L]
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ index.php?category=$1 [L]
~
```

How do I find any "rewrite conditions" added?

I know domain1 has mod_rewrite enabled (its a cms-snews)
Domain2 is just an index.html, cgi-bin and logs dir.

---

### Post by volkswagner on 2011-05-19
Did you add ServerName to the Default?

Perhaps it may help to disable domain1, and see if you can get default and domain2 to play together.

---

### Post by Logansanoh on 2011-05-19
I have dissite the default and no dice either.
I also put a "dummy" servername in default. Also no dice.

If i put domain1 servername in default - default
If i put domain2 servername in default - default
I doubt these would show me different regardless as the directory and index is still pointed to default.

If i disable default - domain1

I have default and domain2 enabled (domain1 disabled) and I still get default.

Im seriously close to giving up. :(

---

### Post by Logansanoh on 2011-05-20
Looks like it might be DNS related.
Trying a fix now...lets see what happens when the caches clear themselves!

---

### Post by tapi0n on 2011-05-21
> **Logansanoh said:**
> Looks like it might be DNS related.
Trying a fix now...lets see what happens when the caches clear themselves!

Since you think it's dns related. 

This might be a stupid thing to suggest. But I've had some things not working because of it, and I know some people who forgot it too which caused things to not work properly either. Have you updated your dns serial?

---

