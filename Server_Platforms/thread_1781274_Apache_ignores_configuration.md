---
title: "Apache ignores configuration"
date: 2011-06-13
forum: Server Platforms
---

### Post by mirshafie on 2011-06-13
Hello folks. Noob calling for help.

I'm trying to get Apache2 to accept some rewrite rules, password protection et.c. but it ignores anything I put into .htaccess. And yes, I have AllowOverride All and no exotic configuration.

At first I thought that my rewrite config was at fault, so I've followed several guides for dummies and for testing purposes settled on the simplest rule I can think of, that of redirecting alice.html to bob.html; two files that look different when opened in a browser.

I have tried adding my directives to the <VirtualHost> and <Directory> sections of my site configs, but no luck.

I finally managed to password protect one of my sites by adding the directives directly into httpd.conf, but nothing less. This leads me to think that there is some more basic problem that I may have overlooked.

I'm running Ubuntu Server 10.04 LTS and Ubuntu Desktop 10.10. Same problem on both machines.

(Although I think this is irrelevant to my problem, I still want to inform you that according to phpinfo() the rewrite module is enabled.)


**So, this is me troubleshooting:**


**/etc/apache2/sites-available/test**
```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/test
        <Directory />
                Options FollowSymLinks
                AllowOverride All
        </Directory>
        <Directory /var/www/test>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
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

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined

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


```
root@mirshafie:~# a2ensite test
Site test already enabled
root@mirshafie:~# ls -l /etc/apache2/sites-enabled/test 
lrwxrwxrwx 1 root root 23 2011-05-30 22:19 /etc/apache2/sites-enabled/test -> ../sites-available/test

```


**/var/www/test/.htaccess**
```
Options +FollowSymLinks
Options +Indexes
RewriteEngine On

RewriteRule ^/alice.html$ bob.html
```


**/etc/apache2/httpd.conf**
This is not what httpd.conf looked like when I started, but as you can see I'm getting desperate.
```
SCGIMount /RPC2 127.0.0.1:5000

AccessFileName .htaccess

<Location /privsite>
AuthName "Private"
AuthType Basic
AuthBasicProvider file
AuthUserFile /home/me/.pwd/htpasswd
Require valid-user
</Location>

<Location /test>
RewriteEngine on
RewriteRule ^alice.html$ bob.html
</Location>

RewriteLog "/var/log/apache2/rewrite.log"
RewriteLogLevel 5
```
The privsite directory is now password protected.


```
root@mirshafie:~# apache2ctl configtest
Syntax OK
root@mirshafie:~# /etc/init.d/apache2 restart
 * Restarting web server apache2
... waiting             [ OK ]
```



With the rewrite directive in httpd.conf, rewrite.log reports stuff like the following. (Without those directives in httpd.conf, nothing.) Yet, even with the httpd.conf directives, no rewriting occurs. (Or maybe I just configured it badly?)

**/var/log/apache2/rewrite.log**
```
my.ip.was.here - - [13/Jun/2011:13:59:11 +0400] [mirshafie.server.net/sid#2b854a945870][rid#2b854aa2d758/initial] (3) [perdir /test/] applying pattern '^alice.html$' to uri '/var/www/test/bob.html'
my.ip.was.here - - [13/Jun/2011:13:59:11 +0400] [mirshafie.server.net/sid#2b854a945870][rid#2b854aa2d758/initial] (1) [perdir /test/] pass through /var/www/test/bob.html
my.ip.was.here - - [13/Jun/2011:13:59:33 +0400] [mirshafie.server.net/sid#2b31f3cfc870][rid#2b31f3fd4bc8/initial] (3) [perdir /test/] applying pattern '^alice.html$' to uri '/var/www/test/bob.html'
my.ip.was.here - - [13/Jun/2011:13:59:33 +0400] [mirshafie.server.net/sid#2b31f3cfc870][rid#2b31f3fd4bc8/initial] (1) [perdir /test/] pass through /var/www/test/bob.html
my.ip.was.here - - [13/Jun/2011:13:59:37 +0400] [mirshafie.server.net/sid#2b31f3cfc870][rid#2b31f3fdabf8/initial] (3) [perdir /test/] applying pattern '^alice.html$' to uri '/var/www/test/alice.html'
my.ip.was.here - - [13/Jun/2011:13:59:37 +0400] [mirshafie.server.net/sid#2b31f3cfc870][rid#2b31f3fdabf8/initial] (1) [perdir /test/] pass through /var/www/test/alice.html
my.ip.was.here - - [13/Jun/2011:14:55:05 +0400] [mirshafie.server.net/sid#2ac2d3ae2870][rid#2ac2d3dc2c08/initial] (3) [perdir /test/] applying pattern '^alice.html$' to uri '/var/www/test/alice.html'
my.ip.was.here - - [13/Jun/2011:14:55:05 +0400] [mirshafie.server.net/sid#2ac2d3ae2870][rid#2ac2d3dc2c08/initial] (1) [perdir /test/] pass through /var/www/test/alice.html
my.ip.was.here - - [13/Jun/2011:14:55:15 +0400] [mirshafie.server.net/sid#2ac2d3ae2870][rid#2ac2d3dbcbd8/initial] (3) [perdir /test/] applying pattern '^alice.html$' to uri '/var/www/test/'
my.ip.was.here - - [13/Jun/2011:14:55:15 +0400] [mirshafie.server.net/sid#2ac2d3ae2870][rid#2ac2d3dbcbd8/initial] (1) [perdir /test/] pass through /var/www/test/
```


Alice is still Alice, Bob is still Bob. Where do I go from here?

And just to be clear. My goal is to to use either the VirtualHost config or .htaccess for these purposes, but if I can get httpd.conf to do it it will solve my problem for now.

---

