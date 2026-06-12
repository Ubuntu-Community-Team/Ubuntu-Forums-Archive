---
title: "Apache2 .htaccess problem viewd all tutorials already, still not working"
date: 2011-04-23
forum: Server Platforms
---

### Post by mushy365 on 2011-04-23
Ok, ive gone through all the tutorials on this and what seems to work for everyone else, does not work for me. 

Firstly. The log file error that happens.

```
[Sat Apr 23 10:22:12 2011] [error] [client 127.0.0.1] File does not exist: /var/www/showthread, referer: http://localhost/
```The .htaccess file that work on my online website, just not working now that ive installed it on my home machine to make it easier to work on

```
Options +FollowSymLinks
RewriteEngine on

RewriteRule ^showthread/([^/\.]+)/?$ index.php?showthread=$1 [L]
RewriteRule ^bulletins/([^/\.]+)/?$ index.php?bulletins=$1 [L]
RewriteRule ^faq/([^/\.]+)/?$ index.php?faq=$1 [L]
RewriteRule ^Newthread/([^/\.]+)/?$ index.php?Newthread=$1 [L]
RewriteRule ^rules/([^/\.]+)/?$ index.php?rules=$1 [L]

RewriteRule ^reply/([^/\.]+)/?$ index.php?replytothread=$1 [L]
RewriteRule ^Add_wiki/([^/\.]+)/?$ wiki.php?add_Wiki=$1 [L]
RewriteRule ^Show_wiki/([^/\.]+)/?$ wiki.php?display_Wiki=$1 [L]
RewriteRule ^Edit_wiki/([^/\.]+)/?$ wiki.php?editwiki=$1 [L]
RewriteRule ^History/([^/\.]+)/?$ wiki.php?history=$1 [L]
RewriteRule ^page/([^/\.]+)/?$ pages.php?page=$1 [L]

ErrorDocument 404 /notfound.php
```
Ive changed the /etc/apache2/sites-available/default file to 

```
DocumentRoot /var/www
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>

```Note ive also tried it will 'all' instead of 'All'

I reload apache and then restart apache. Still get the same errors. Also for some reason on my latest reload and restart apache commands i get an error

```
brian@brian-00000000000000000000000:~$ /etc/init.d/apache2 reload
 * Reloading web server config apache2                                          httpd not running, trying to start
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
Action 'graceful' failed.
The Apache error log may have more information.
```which is really annoying.

---

### Post by falko on 2011-04-23
It seems as if there's another process listening on port 80. You can check that with ```
netstat -tap
```

---

### Post by mushy365 on 2011-04-23
That brings up alot of info. Nothing about port 80 as far as i can see. The error with restarting apache isnt my main priority though. Its getting the htaccess to work, im sure i could restart the system to sort out apache

---

### Post by mushy365 on 2011-04-23
anyone? Further googling has produced nothing. So frustrated.

---

### Post by SeijiSensei on 2011-04-23
> brian@brian-00000000000000000000000:~$ /etc/init.d/apache2 reload

You need to run this command with sudo:

```
sudo /etc/init.d/apache2/reload
```

---

### Post by mushy365 on 2011-04-23
Thanks, that sorts out why that wasnt working. Anyone any ideas about the .htaccess file? Still wont work.

---

