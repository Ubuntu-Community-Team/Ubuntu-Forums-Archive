---
title: "Webmail subdomain got problem!"
date: 2011-03-16
forum: Server Platforms
---

### Post by Kozley on 2011-03-16
Before I used webmail subdomain webmail.mydomain.com was work. When I set up redirect non-www to www using rewrite option to try make empty subdomain to www and seem it doesn't works then I removed redirect options and disable mod_rewrite and now I cannot get webmail.mydomain.com works again. I have rebooted apache.

How I could get subdomain works back?

---

### Post by falko on 2011-03-16
Did you clear your browser cache?

---

### Post by Kozley on 2011-03-16
> **falko said:**
> Did you clear your browser cache?
Yes, I did. Same resultats.

---

### Post by falko on 2011-03-16
Does it happen in other browsers as well?

What exactly did you change in your Apache configuration?

---

### Post by Kozley on 2011-03-16
> **falko said:**
> Does it happen in other browsers as well?

What exactly did you change in your Apache configuration?
It does same thing.

Here's /etc/apache2/httpd.conf:
```
NameVirtualHost *:80

<VirtualHost *:80>

DocumentRoot /var/www
<Directory />
Options FollowSymLinks
 AllowOverride None
</Directory>
</VirtualHost>

<VirtualHost *:80>
ServerName first.mydomain.com
DocumentRoot /var/www/first
</VirtualHost>

<VirtualHost *:80>
ServerName second.mydomain.com
DocumentRoot /var/www/second
</VirtualHost>
```etc/apache2/conf.d/squirrelmail.conf:
```
Alias /squirrelmail /usr/share/squirrelmail

<Directory /usr/share/squirrelmail>
  Options Indexes FollowSymLinks
  <IfModule mod_php5.c>
    php_flag register_globals off
  </IfModule>
  <IfModule mod_dir.c>
    DirectoryIndex index.php
  </IfModule>

  # access to configtest is limited by default to prevent information leak
  <Files configtest.php>
    order deny,allow
    deny from all
    allow from 127.0.0.1
  </Files>
</Directory>

# users will prefer a simple URL like http://webmail.example.com
<VirtualHost *:80>
  DocumentRoot /usr/share/squirrelmail
  ServerName webmail.mydomain.com
</VirtualHost>

# redirect to https when available (thanks omen@descolada.dartmouth.edu)
#
#  Note: There are multiple ways to do this, and which one is suitable for
#  your site's configuration depends. Consult the apache documentation if
#  you're unsure, as this example might not work everywhere.
#
#<IfModule mod_rewrite.c>
#  <IfModule mod_ssl.c>
#    <Location /squirrelmail>
#      RewriteEngine on
#      RewriteCond %{HTTPS} !^on$ [NC]
#      RewriteRule . https://%{HTTP_HOST}%{REQUEST_URI}  [L]
#    </Location>
#  </IfModule>
#</IfModule>

```I had edit redirect subdomain with using mod_rewrite in httpd.conf before it removed:
```
RewriteEngine on
RewriteCond %{HTTP_HOST} !^www.*$ [NC]
RewriteRule ^/.+www\/(.*)$ http://www.%{HTTP_HOST}/$1 [R=301,L]
```

---

### Post by BkkBonanza on 2011-03-16
When you removed the rewrite rule make sure you didn't introduce a typo/mistake. If you restart and there's an error it may prevent apache from using the new conf. Check the apache error log for anything that may tell you the problem. If the rewrite rule is removed it should no longer have an effect on the subdomains, and they should work as before.

Once you have that sorted out I'd suggest you don't use rewrite to map subdomains as it introduces work for every page hit. Use a CNAME entry on your DNS settings to do this instead. Add a CNAME for *.domain.com -> [www.doman.com](www.doman.com) and be sure that the webmail.domain.com one comes first so it doesn't get caught by the * one. This allows the subdomain mapping to be done at the DNS level and hence no extra work on your web server.

---

### Post by Kozley on 2011-03-16
Okay, I have looked on error log of apache2 and didn't found any error about subdomain. So I create new subdomain on DNS entry and replace it on /etc/apache2/conf.d/squirrelmail.conf to new subdomain, it works now. It seems as old subdomain is already crashed after rewrite removed. Well, I do use the new subdomain. I can say thank you for the help.

EDIT: When I created new subdomain was work little time but now it doesn't works!
Now I can see on error log:
```
[Thu Mar 17 01:57:57 2011] [notice] caught SIGTERM, shutting down
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Thu Mar 17 01:57:58 2011] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.7 with Suhosin-Patch configured -- resuming normal operations
[Thu Mar 17 01:59:10 2011] [error] [client 212.116.72.67] File does not exist: /usr/share/squirrelmail/favicon.ico
[Thu Mar 17 01:59:13 2011] [error] [client 212.116.72.67] File does not exist: /usr/share/squirrelmail/favicon.ico
```

EDIT2: I added subdomain to /etc/hosts with internal ipaddress and it does works only on local machine. Which configuration needs to change it to work normal?

---

### Post by Kozley on 2011-03-17
Ok, I have reinstalled apache2 and create new subdomain on DNS entry. Now it works but don't know if it should works permanently.

---

