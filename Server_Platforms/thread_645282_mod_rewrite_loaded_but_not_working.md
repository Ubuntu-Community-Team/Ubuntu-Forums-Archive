---
title: "mod_rewrite loaded but not working"
date: 2007-12-19
forum: Server Platforms
---

### Post by Zarathu on 2007-12-19
I have seriously followed every online tutorial and nothing is working at all.  I know that mod_rewrite is loaded, but it doesn't give a rat's *** about the .htaccess

Here are some configs:

apache2.conf:
[http://www.thesarcasm.com/paste.php?id=2341125](http://www.thesarcasm.com/paste.php?id=2341125)

/var/www/.htaccess:  (the root of my PHP files)
```
RewriteEngine on
RewriteBase /
RewriteCond %{HTTP_HOST}   ^myusername\.homeunix\.com$
RewriteRule ^/(.*)         http://google.com/$1 [L,R]
```

/etc/apache2/sites-enabled/000-default:
[http://www.thesarcasm.com/paste.php?id=7271524](http://www.thesarcasm.com/paste.php?id=7271524)

```
root@jesus:/etc/apache2# ls -l mods-available/ mods-enabled/ | grep "rewrite"
-rw-r--r-- 1 root root   66 2007-08-16 17:45 rewrite.load
-rw-r--r-- 1 root root 233 2007-12-19 21:00 rewrite.load
root@jesus:/etc/apache2#
```

mods-available/rewrite.load:
```

LoadModule rewrite_module /usr/lib/apache2/modules/mod_rewrite.so

```

mods-enabled/rewrite.load:
```
LoadModule rewrite_module /usr/lib/apache2/modules/mod_rewrite.so

<IfModule mod_rewrite.c>
RewriteEngine On
RewriteRule ^myusername\.homeunix\.com$ http://www.google.com [R]
</IfModule>
```

Any ideas?

---

### Post by jjross on 2007-12-19
read this link and it should explain what is going on with your 
[.htaccess]("http://www.reallylinux.com/docs/htaccess.shtml")
it is ignored until you change your httpd file to allow it to use it
Here is another good link with even better information
[http://www.javascriptkit.com/howto/htaccess.shtml]("http://www.javascriptkit.com/howto/htaccess.shtml")

---

### Post by Zarathu on 2007-12-19
Odd.

Alright, so I put "AllowOverride AuthConfig" in the /var/www <Directory>.

Now, if I have even the slightest thing in my /var/www/.htaccess, it gives a 500 response code and says "<Whatever> is not allowed here." in the error.log.

---

### Post by jjross on 2007-12-19
i just found this
> # AllowOverride controls what directives may be placed in .htaccess files.
# It can be "All", "None", or any combination of the keywords:
# Options FileInfo AuthConfig Limit
#
AllowOverride All

The all directive allows all directives to be placed within an .htaccess file

about line 328 you will find:

# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives. See also the AllowOverride
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

AccessFileName defines what the access filename will be ...I imagine you can name it anything you want but .htaccess is the norm. 

I think you need to change it to "all"

---

### Post by Zarathu on 2007-12-19
This is from RewriteLog:

[http://www.thesarcasm.com/paste.php?id=7199137](http://www.thesarcasm.com/paste.php?id=7199137)

I got it reading from the .htaccess file now, which is great.

.htaccess:
```
RewriteEngine on
RewriteBase /
RewriteRule ^(.*)\.myusername\.homeunix\.com$ myusername.homeunix.com/blog/$1/index.php
```


Still not working, though. :/

---

### Post by Zarathu on 2007-12-20
Resolved.  I win.

```
me > mod_rewrite
```

---

