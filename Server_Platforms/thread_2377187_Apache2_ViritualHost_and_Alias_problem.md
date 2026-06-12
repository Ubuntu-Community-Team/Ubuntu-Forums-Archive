---
title: "Apache2 ViritualHost and Alias problem"
date: 2017-11-10
forum: Server Platforms
---

### Post by cazz on 2017-11-10
Hi
I have work with apache and sometime with viritualhost when Iwant to redirect a domain to another webserver at home
But I have never work with alias like this and never ever laravel.

I person I know have help me to create a website and it use laravel so I did have to start read a little about it how to install and that.
well I have came so far so I think I have install the laravel but now is time to access to it and now I have problem.

to make sure that I did not have install the laravel wrong I create a text site and page that was just a simple HTML but even that I can't access.
I have read and search alot but never got it to work.

That I have done is this.

The default folder is ```
/var/www/html/
``` and I like to have it like that so when I use my IP nummer x.x.x.x/hostname I can see what I have put in the default folder.
Now I have create ```
/var/www/test/
``` and I like to access it from [HTML]x.x.x.x/test[/HTML] or [HTML]hostname/test[/HTML]

I have create a conf file in sites-available and I have try

```
<VirtualHost *:80>
  ServerName x.x.x.x
  Alias /text /var/www/test
  DocumentRoot /var/www/test
  <Directory "/var/www/test">
    AllowOverride all
    Order allow,deny
    Allow from all
  </Directory>
</VirtualHost>
```

and after that 

```
sudo a2ensite test.conf
```

and in the test folder I have 

```
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /test/
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ index.php/$1 [L]
</IfModule>
```

Have also try other settings but never got it to work.

Not sure what more I can do??

---

### Post by SeijiSensei on 2017-11-10
>   Alias /text /var/www/test
  DocumentRoot /var/www/test
  <Directory "/var/www/test">


First, the Alias directive has a typo; it should be /test.

To have the default site still be stored in /var/www/html, set the DocumentRoot and Directory directives to /var/www/html.  Now a request for 

[http://ip.addr.of.server/](http://ip.addr.of.server/) 

will return the contents of /var/www/html, while a request for

[http://ip.addr.of.server/test/](http://ip.addr.of.server/test/)

will return the contents of /var/www/test.

---

### Post by cazz on 2017-11-10
Hi thanks for the replay
I can't access the server right now but I have a Apache2 on a ubuntu server at home and I have create a config file there (test.conf) and I have notice something

when I have this

```
<VirtualHost *:80>
  ServerName domain.se
  ServerAlias x.x.x.x
  Alias /test /home/konto/www/test
  DocumentRoot /home/konto/www/test
  <Directory "/home/konto/www/test">
    AllowOverride all
    Order allow,deny
    Allow from all
  </Directory>
</VirtualHost>
```

then I can connec to test folder with [http://x.x.x.x/test](http://x.x.x.x/test) but not [http://domain.se/test](http://domain.se/test)

and when I change the code a little

```
<VirtualHost *:80>
  ServerName domain.se
  ServerAlias domain.se
  Alias /test /home/konto/www/test
  DocumentRoot /home/konto/www/test
  <Directory "/home/konto/www/test">
    AllowOverride all
    Order allow,deny
    Allow from all
  </Directory>
</VirtualHost>
```

I still can't connect to the folder with [http://domain.se/test](http://domain.se/test)

Maybe is something in the default domain.se.conf that make it stop working

```
<VirtualHost *:80>
    ServerAdmin info@domain.se
    ServerName domain.se
    ServerAlias www.domain.se
    DocumentRoot /home/konto/www/public
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

---

### Post by SeijiSensei on 2017-11-10
Sorry.  You need a corresponding <Directory "/var/www/test"> stanza as well.

```

<VirtualHost *:80>
[stuff]

DocumentRoot /var/www/html
<Directory "/var/www/html">
    [stuff]
</Directory>

Alias /test /var/www/test
<Directory "/var/www/test">
    [stuff]
</Directory>

</VirtualHost>

```

---

### Post by cazz on 2017-11-10
Thanks, I did not notice that I did not have any Directory in my default config file and now when I have done that and edit a little I got it to work :)

---

