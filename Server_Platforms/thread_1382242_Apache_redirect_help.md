---
title: "Apache redirect help"
date: 2010-01-15
forum: Server Platforms
---

### Post by theRemix on 2010-01-15
Hi, 

what is the correct regex to match all files that is **not** a static binary file (.jpg|.png|.gif|.mov|.flv|.swf) 

and then rewrite it to route to a different subdomain ?

RewriteCond %{REQUEST_URI} FANCYREGEXHERE [NC] 
RewriteRule .+ http://assets.mydomain.com%{REQUEST_URI} 

and how do you put this in the global apache config that applies to every vhost so that it rewrite 
http(s)://anysubdomain.primarydomain.tld/request 
to 
[http://assets.anysubdomain.primarydomain.tld/request](http://assets.anysubdomain.primarydomain.tld/request) 


thanks in advance.

---

### Post by Ilalmi on 2010-01-17
Hi,

put the following lines into a file /etc/apache2/mods-available/rewrite.conf:
```
RewriteEngine on
RewriteCond %{REQUEST_URI} !(\.(jpg|gif|png|mov|flv|swf))  [NC]
RewriteRule .+ http://assets.mydomain.com%{REQUEST_URI} [L]
```
and put a symlink to that file into /etc/apache2/mods-enabled/.
Now every virtual host needs the lines 
```
RewriteEngine on
RewriteOptions inherit
```
inside its context, to be able to use those rules.
That should do it.

---

