---
title: "url rewriting not working"
date: 2010-06-16
forum: Server Platforms
---

### Post by bigelow13 on 2010-06-16
Hi everybody

I aleardy set up an url rewriting before, but this time it does not seem to be working...
To module is installed and activated
I created an htaccess file in [http://localhost/entrepreneur/](http://localhost/entrepreneur/) 
contaning the following code: 
```
Options +FollowSymLinks
RewriteEngine On

RewriteRule ^pet-care/$ index.html [R]
```but when i try to visit [http://localhost/entrepreneur/pet-care/](http://localhost/entrepreneur/pet-care/), apache tells me the page is not found. 

any help would be welcome! 

thank you.

---

### Post by dapperdanny77 on 2010-06-16
> **bigelow13 said:**
> Hi everybody

```
Options +FollowSymLinks
RewriteEngine On

RewriteRule ^pet-care/$ index.html [R]
```but when i try to visit [http://localhost/entrepreneur/pet-care/](http://localhost/entrepreneur/pet-care/), apache tells me the page is not found. 

any help would be welcome! 

thank you.

```

^pet-care/$ matches http://localhost/pet-care which delivers a 404

the following should work ..?
RewriteRule ^entrepreneur/pet-care/$ index.html [R]

```

---

### Post by bigelow13 on 2010-06-17
thanks for your reply, but this is not working neither! I am still getting a 404
any other ideas?

---

### Post by dapperdanny77 on 2010-06-17
check your apache error logs - usually /var/log/apache2/ - you can also enable logging for the rewrite engine.
find more on [http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html](http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html)

---

### Post by bigelow13 on 2010-06-19
I found a solution elsewhere;

.htaccess fils were not read by apache, because it's configuration files weren't allowing an htaccess to override previoulsy given instructions. I had to open /etc/apache2/sites-available/default and replace AllowOverride None by AllowOverride All

thank you all

---

