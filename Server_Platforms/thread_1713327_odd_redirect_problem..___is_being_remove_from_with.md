---
title: "odd redirect problem..  / is being remove from within url"
date: 2011-03-23
forum: Server Platforms
---

### Post by kutu62 on 2011-03-23
Hey guys.. new to the forums but not web servers.. but I'm stumped and need some help here in a bad way.



 I set up a 301 redirect
from:
Redirect permanent /category/mlb/depth-chart/
to:
[http://domain.com/category/fantasy-basebal](http://domain.com/category/fantasy-basebal)**l/d**epth-chart/


 notice the forward slash in the "to" url after the word baseball


 then when I visit category/mlb/depth-chart/ 
 I get redirected to the below url
 [http://domain.com/category/fantasy-basebal](http://domain.com/category/fantasy-basebal)**ld**epth-chart/


 notice the redirect removed the forward slash between "baseball" and "depth"


 I tried this in both my sites-available and in a .htaccess - same results
I tried adding quotes around the url
I tried adding html markup to replace the /
I tried adding double //
Nothing works for me..
 If anyone has some ideas please please please toss them my way.
Thanks!! 





Ubuntu verision 10.10
Apache version 2.2
Wordpress blog 3.1

---

### Post by BkkBonanza on 2011-03-23
Please show your redirect code so someone can help out. Not much anyone can say without seeing the code.

---

### Post by kutu62 on 2011-03-24
duh.. good idea

this is my htaccess

```
# BEGIN WPSuperCache
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /
AddDefaultCharset UTF-8
RewriteCond %{REQUEST_URI} !^.*[^/]$
RewriteCond %{REQUEST_URI} !^.*//.*$
RewriteCond %{REQUEST_METHOD} !POST
RewriteCond %{QUERY_STRING} !.*=.*
RewriteCond %{HTTP:Cookie} !^.*(comment_author_|wordpress_logged_in|wp-postpass_).*$
RewriteCond %{HTTP:X-Wap-Profile} !^[a-z0-9\"]+ [NC]
RewriteCond %{HTTP:Profile} !^[a-z0-9\"]+ [NC]
RewriteCond %{HTTP:Accept-Encoding} gzip
RewriteCond %{DOCUMENT_ROOT}/wp-content/cache/supercache/%{HTTP_HOST}/$1/index.html.gz -f
RewriteRule ^(.*) "/wp-content/cache/supercache/%{HTTP_HOST}/$1/index.html.gz" [L]
RewriteCond %{REQUEST_URI} !^.*[^/]$
RewriteCond %{REQUEST_URI} !^.*//.*$
RewriteCond %{REQUEST_METHOD} !POST
RewriteCond %{QUERY_STRING} !.*=.*
RewriteCond %{HTTP:Cookie} !^.*(comment_author_|wordpress_logged_in|wp-postpass_).*$
RewriteCond %{HTTP:X-Wap-Profile} !^[a-z0-9\"]+ [NC]
RewriteCond %{HTTP:Profile} !^[a-z0-9\"]+ [NC]
RewriteCond %{DOCUMENT_ROOT}/wp-content/cache/supercache/%{HTTP_HOST}/$1/index.html -f
RewriteRule ^(.*) "/wp-content/cache/supercache/%{HTTP_HOST}/$1/index.html" [L]
</IfModule>
# END WPSuperCache
# BEGIN WordPress
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
# END WordPress
```


*******************************************************************8
this is my vhost (sites-enabled)

```
<VirtualHost 123.123.123.123:80>
    ServerAdmin webmaster@absolutenetworks.biz
    DocumentRoot "/var/www/domain"
    ServerName domain.com 
    ServerAlias www.domain.com
    ErrorLog "/var/log/apache2/domain.com-error_log"
    CustomLog "/var/log/apache2/domain.com-access_log" combined
Redirect permanent /category/mlb/ http://domain.com/category/fantasy-baseball
Redirect permanent /category/mlb/depth-chart/ http://domain.com/category/fantasy-baseball/depth-chart/
</VirtualHost>
```
first redirect works fine in vhost - second one removed that slash between the words baseball and depth

---

### Post by BkkBonanza on 2011-03-24
I don't think the second one is having any effect. 

I think when you test the second one with 

/category/mlb/depth-chart/ 

it's getting picked up by the first and adding depth-chart/ onto it's target of 

[http://domain.com/category/fantasy-baseball](http://domain.com/category/fantasy-baseball)

to give

[http://domain.com/category/fantasy-baseballdepth-chart/](http://domain.com/category/fantasy-baseballdepth-chart/)

Try adding a / to the end of the first redirect and removing the second one, or alternately, reversing the order of the redirects to grab the more specific one first.

---

### Post by kutu62 on 2011-03-24
I think that fixed it.. I'll add my full redirect list tonight and let us know then mark this resolved. Thank you!!

---

