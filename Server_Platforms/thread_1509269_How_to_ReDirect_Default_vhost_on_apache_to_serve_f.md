---
title: "How to ReDirect Default vhost on apache to serve from different directory"
date: 2010-06-14
forum: Server Platforms
---

### Post by tapas_mishra on 2010-06-14
I have 5 websites running on a webserver.
I read Apache docs Apache serves the vhost file in alphabetical order
of name of vhost file.The default ServerName which will serve is the one which comes alphabetically first.

I have a few subdomains on main domain

[http://mydomain.com](http://mydomain.com)

as follows
```

http://site1.mydomain.com
http://site2.mydomain.com
http://site3.mydomain.com
http://site4.mydomain.com

```
in one of them which is served by default I want to redirect to
correct [http://mydomain.com](http://mydomain.com)
so I added in [http://site1.mydomain.com](http://site1.mydomain.com)

the ReWriteRule in vhost of site1.mydomain.com as follows

```

 ReWriteRule ^/mydomain.com$ /var/www/index.html [NC,L]
 ReWriteRule ^/mydomain.com/$ /var/www/index.html [NC,L]

```
I checked the ReWriteLogs by

ReWriteLog "/var/log/apache2/mydomain_rewrite_log"
ReWriteLogLevel 9

could not understand much.

My problem is the ReWriteRule did not do as I wanted it to do.So I
have written some thing in correct.
Can some one help to find what is the problem in above ReWriteRule?

---

### Post by Ryan Dwyer on 2010-06-14
RewriteEngine on
RewriteRule .* [http://domain.com/](http://domain.com/)

---

### Post by tapas_mishra on 2010-06-14
Ok is there any way that I can redirect to a different file to a particular request.

---

### Post by Ryan Dwyer on 2010-06-14
RewriteEngine on
RewriteRule ^/file [http://mydomain.com/blah](http://mydomain.com/blah)
RewriteRule .* [http://mydomain.com/](http://mydomain.com/)

---

### Post by tapas_mishra on 2010-06-14
> **Ryan Dwyer said:**
> RewriteEngine on
RewriteRule ^/file [http://mydomain.com/blah](http://mydomain.com/blah)
RewriteRule .* [http://mydomain.com/](http://mydomain.com/)
What is the mistake in ReWrite Rules I wrote in the first post in this thread.

---

### Post by Ryan Dwyer on 2010-06-14
These are the rules you posted:

ReWriteRule ^/mydomain.com$ /var/www/index.html [NC,L]
ReWriteRule ^/mydomain.com/$ /var/www/index.html [NC,L]

Those rules will match [http://site1.mydomain.com/mydomain.com](http://site1.mydomain.com/mydomain.com). The rules take effect on the REQUEST URI (part after the hostname) unless you use a RewriteCond with the HTTP_HOST variable (I don't know the exact syntax).

Additionally, the target URL should not be a Unix filesystem path. It should be a frontend URL, just like what you'd put in a hyperlink.

---

### Post by tapas_mishra on 2010-06-15
[Here]("http://http://www.askapache.com/htaccess/crazy-advanced-mod_rewrite-tutorial.html") is a link to a tutorial which I tried I think you are also saying some thing similar.

```

RewriteEngine On
RewriteBase /
 
RewriteCond %{HTTP_HOST} !^www\.askapache\.com$ [NC]
RewriteRule .+ http://www.askapache.com%{REQUEST_URI}

```
I could not understand what is the mistake in the above rule?
Can some one point what is the error which the tutorial is trying to tell.

---

