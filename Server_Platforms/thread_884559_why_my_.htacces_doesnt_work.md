---
title: "why my .htacces doesnt work?"
date: 2008-08-09
forum: Server Platforms
---

### Post by maxidrom11 on 2008-08-09
I want to remove www. in mydomain.com using 301 redirect with .htaccess but it doesnt work for some reason :confused:

In my **Apache 2.** all needed .htaccess directives enabled I guess
**mod_rewrite** is enabled - I am sure
```

# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#

AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being 
# viewed by Web clients. 
#
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>


```

I set up Virtual hosting for mydomain.com 

```

DocumentRoot "/var/www/path"
ServerName mydomain.com
ServerAdmin webmaster@domain.com
<Directory "/var/www/path">
Options Indexes FollowSymLinks MultiViews
		**AllowOverride All**
		Order allow,deny
		allow from all
</Directory>

```

my .htaccess file looks like this:
```

DirectoryIndex index.php
<FilesMatch .\.php>
ForceType application/x-httpd-php
</FilesMatch>
Options -MultiViews -Indexes +FollowSymlinks
RewriteEngine On
RewriteBase /
RewriteRule ^adser|ref|product\.php - [L]
RewriteCond $1 !(\.css)|(\.js)|(\.ico)|(\.swf)|(\.jpg)|(\.png)|(\.gif)|(^widgets.*)$ [NC]
RewriteRule ^(.*)$ index.php [QSA,NC,L]
[COLOR="Red"]RewriteEngine On
RewriteCond %{HTTP_HOST} ^www.mydomain.com$ [NC]
RewriteRule ^(.*)$ http://mydomain.com/$1 [R=301,L][/COLOR]
```

I dont understand why it doest redirect my site from [www.mydomain.com](www.mydomain.com) to mydomain.com

---

### Post by maxidrom11 on 2008-08-10
problem solved 
my .htaccess should look like this:
```

DirectoryIndex index.php
<FilesMatch .\.php>
ForceType application/x-httpd-php
</FilesMatch>
Options -MultiViews -Indexes +FollowSymlinks
RewriteEngine On
RewriteBase /
[COLOR="Red"]RewriteCond %{HTTP_HOST} ^www.example.com$ [NC]
RewriteRule ^(.*)$ http://example.com/$1 [R=301,L][/COLOR]
RewriteRule ^adser|ref|product\.php - [L]
RewriteCond $1 !(\.css)|(\.js)|(\.ico)|(\.swf)|(\.jpg)|(\.png)|(\.gif)|(^widgets.*)$ [NC]
RewriteRule ^(.*)$ index.php [QSA,NC,L]

```

---

### Post by Dedoimedo on 2008-08-10
Hi,
Good that you've solved it out, now a simple question:
Why didn't you try using the redirect directive?
Dedoimedo

---

### Post by maxidrom11 on 2008-08-10
> **Dedoimedo said:**
> Hi,
Good that you've solved it out, now a simple question:
Why didn't you try using the redirect directive?
Dedoimedo

'cos nobody posted a reply to my message 

So let me see how my Redirect derective should look if I want redirect my site from [www.mydomain.com](www.mydomain.com) to mydomain.com

by the way I dont want to redirect only one page

---

### Post by Dedoimedo on 2008-08-10
Hello,

[http://httpd.apache.org/docs/2.0/mod/mod_alias.html#redirect](http://httpd.apache.org/docs/2.0/mod/mod_alias.html#redirect)


Redirect works for any domain + all subdomains, so that my be what you want. Furthermore, you can use virtual hosts for multiple domains.

You can try my Apache guide, there might be useful answers in there you might like ...

Regards,
Dedoimedo

---

### Post by maxidrom11 on 2008-08-11
ok 
I used this:
```
Redirect permanent http://www.domain.tld/ http://domain.tld/

```

it doesnt work at all :confused:

---

### Post by Dedoimedo on 2008-08-11
Hello,
Is www a CNAME entry in your DNS record?
If so, then you need to remove it for this to work.
Dedoimedo

---

