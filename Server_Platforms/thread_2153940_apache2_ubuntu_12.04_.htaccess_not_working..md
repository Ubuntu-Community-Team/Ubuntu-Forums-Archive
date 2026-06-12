---
title: "apache2 ubuntu 12.04 .htaccess not working."
date: 2013-06-12
forum: Server Platforms
---

### Post by louis vitton on 2013-06-12
Hi guys,
I am having an issue with my system. I am using ubuntu 12.04.
I am using laravel 4 and the .htaccess is posted in the public folder with no other htaccess in either root dir or public folders.
I can access dev.example.com no issues but then when i go to any link i am having to add index.php to make the link work.
Example: 
dev.example.com/user/login (This link doesnt work)
dev.example.com/index.php/user/login (This link does work)
forgive the spaces i cannot post links


I transfered the files to my wamp system on my laptop worked no issue and normally. Not sure where my error is though on my Ubuntu system.
Here are a list of mods enabled also;
```
alias.conf          authz_groupfile.load  deflate.conf  mime.conf         reqtimeout.conf  ssl.load
alias.load          authz_host.load       deflate.load  mime.load         reqtimeout.load  status.conf
auth_basic.load     authz_user.load       dir.conf      negotiation.conf  rewrite.load     status.load
auth_mysql.load     autoindex.conf        dir.load      negotiation.load  setenvif.conf    wsgi.conf
authn_file.load     autoindex.load        env.load      php5.conf         setenvif.load    wsgi.load
authz_default.load  cgi.load              headers.load  php5.load         ssl.conf

```

*rewrite mod is enabled 
root@h:/etc/apache2/mods-enabled# a2enmod rewrite
Module rewrite already enabled


*htaccess file
```
<IfModule mod_rewrite.c>
    Options +FollowSymLinks
    RewriteEngine On
</IfModule>
<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteBase /
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteRule ^(.*)$ index.php/$1 [L]
</IfModule>



```*virtual host details
```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName dev.example.com
        ServerAlias www.dev.example.com
        DocumentRoot /var/Laravel-4-Bootstrap-Starter-Site-master/public
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/Laravel-4-Bootstrap-Starter-Site-master/public/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

```

Thanks for any help in advance.

---

### Post by newbie-user on 2013-06-13
Seems as though you have a folder called "index.php" in which your other web documents reside. What are the contents of /var/Laravel-4-Bootstrap-Starter-Site-master/public/?

---

### Post by louis vitton on 2013-06-13
the public folder holds the htaccess file aswell as the index.php - the laravel framework uses this to launch the applocation but it isnt required in the urls.
it should just ignore the index.php in the urls and allow me to access the page dev.example.com/login but currently get dev.example.com/index.php/login
it works normally on wamp on windows so think itmay be my apache2 config or mods affectingit.

---

### Post by SeijiSensei on 2013-06-13
The htaccess file is disabled by default in Ubuntu.  The preferred practice if you control your own server is to place any directives that would appear in .htaccess in the <Directory> stanza for the DocumentRoot in the virtual host's configuration /etc/apache2/sites-available/.

If you really need .htaccess, then you'll have to replace "Allow Override None" with "Allow Override All" in /etc/apache2/sites-available/default or a more nuanced list from the [options here]("http://httpd.apache.org/docs/current/mod/core.html#allowoverride").  Then restart Apache.

---

### Post by louis vitton on 2013-06-14
Thanks for that info I will try that out tonight.

---

### Post by louis vitton on 2013-06-14
Thank you for the help the issue has been resolved with the above post

---

