---
title: "Making Apache server use SSL only"
date: 2007-05-30
forum: Server Platforms
---

### Post by sxturbo on 2007-05-30
Hey guys. I'm running a ubuntu 6.06.1 server with apache2.

Everything is up and running fine, but I want to only run SSL on here. I dont want other people on the network able to get in with just http.

I have configured /etc/apache2/ports.conf like
```
Listen 443

```

I have configured /etc/apache2/sites-available/default , and ssl to be the following

```

NameVirtualHost *:443
<VirtualHost *:443>
        ServerAdmin    dontworryaboutmyaddy ;)

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
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>
SSLEngine On
SSLCertificateFile /etc/apache2/ssl/apache.pem

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

I just can't get the site to show up HTTPS by default. If i type the IP or device name in the browser it does nothing unless I specify HTTPS in front.

---

### Post by dfreer on 2007-05-30
The way you have it set up now, it will only respond to port 443, hence the reason why you can only reach it by specifying https in front. One thing you should look into is port redirection. Or, you could open port 80 back up, and create a index.php file (assuming you have php enabled) in the port 80 site that simply redirects traffic to port 443. For example:

<?php
// This is your index.php page

// This simply redirects to a page of your choice
header('Location: https://dontworry.aboutmyaddy.com');
?>

The more correct way would be port 80 redirection, but yay for php!

---

### Post by sxturbo on 2007-05-30
got it. thanks for your help :D

---

### Post by kakao on 2007-10-20
even better would be some redirect lines in the default config file for :80. Some virtual host like this in addition to the *:443 one:

```

NameVirtualHost *:80
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	
	RewriteEngine   on
	RewriteCond     %{SERVER_PORT} ^80$
	RewriteRule     ^/(.*)$ https://%{SERVER_NAME}/%{N}$1 [L,R]
	RewriteLog      "/var/log/apache2/rewrite.log"
	RewriteLogLevel 2
</VirtualHost>

```

For more details see [Apache2 RewriteRule]("http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html#rewriterule") and [list of example rewrites]("http://httpd.apache.org/docs/2.0/misc/rewriteguide.html"). Some comments
[LIST]
[*] 'L' makes this the last rule for rewrites
[*] 'R' makes apache responde with 302 (MOVED TEMPORARILY) and new URI/URL is passed to the client, i.e. change is not made silently.
[*] ${N} is replaced by whatever ^/(.*)$ found in the URI/URL
[/LIST]

Maybe one could even define a virtual host for everything but *:443 but I don't know how. If one has a very simple and private (read localhost only) setup a line like
```

RedirectMatch ^/$ https://localhost/$

```
could do but that's not tested. Note that the default that comes with the Ubuntu package has to be disabled (or any other virtual host *).

---

