---
title: "301 Redirects"
date: 2009-02-04
forum: Server Platforms
---

### Post by mregister on 2009-02-04
Hello All,

Does anyone know of a good tutorial on how to setup a 301 redirect with ubuntu/apache2 ? And let me say that I am not entirely sure that a 301 is what I need. What I am trying to accomplish is have example.com go to [www.example.com](www.example.com). From what I have read I should create an .htaccess file with:
```
RewriteEngine on

RewriteCond %{HTTP_HOST} ^example.com [NC]
RewriteRule ^(.*) http://www.example.com/$1 [L,R=301]


```

but when i do this example.com comes up with an internal server error page. Should I create a virtual host example.com first then use .htaccess?

Thanks to all,

Mark

---

### Post by Thirtysixway on 2009-02-04
From the apache web site
[http://httpd.apache.org/docs/2.0/misc/rewriteguide.html](http://httpd.apache.org/docs/2.0/misc/rewriteguide.html)
```

RewriteEngine on

RewriteCond %{HTTP_HOST}   !^www\.example\.com [NC]
RewriteCond %{HTTP_HOST}   !^$
RewriteRule ^/(.*)         http://www.example.com/$1 [L,R]

```

Not sure how to force a 301 but hope this sort of helps.  It looks to only have some small changes to what you have currently, try it out.

---

### Post by mregister on 2009-02-04
No dice. This is not a heavly configured machine and [www.example.com](www.example.com) comes up fine but still can't get the example.com to [www.example.com](www.example.com) to work. Here is my .htaccess file:
```
RewriteEngine on

RewriteCond %{HTTP_HOST} !^www\.example\.com [NC]
RewriteCond %{HTTP_HOST} !^$
RewriteRule ^/(.*)       http://www.example.com/$1 [L,R]


```

I still get the internal server error page when I try to load example.com. 
I checked the server error log and noting about it. From all that I have read, the above .htaccess file should work. I am wondering if I should setup a virtual host and then just copy /etc/apache2/sites-available/default /etc/apache2/sites-available/example then enalbe the site? But it just seems the easiest and best way is to use .htaccess but it's just not working.

---

### Post by volkswagner on 2009-02-04
This [301 Redirect How-to]("http://www.webconfs.com/how-to-redirect-a-webpage.php") helped me a lot.  It explains various servers.

I think for Linux based you can use the .htaccess method.

---

### Post by Thirtysixway on 2009-02-04
> **volkswagner said:**
> This [301 Redirect How-to]("http://www.webconfs.com/how-to-redirect-a-webpage.php") helped me a lot.  It explains various servers.

I think for Linux based you can use the .htaccess method.

From the page:
```

Options +FollowSymlinks
RewriteEngine on
rewritecond %{http_host} ^domain.com [nc]
rewriterule ^(.*)$ http://www.domain.com/$1 [r=301,nc] 
```

---

### Post by mregister on 2009-02-04
Ok thanks Thirtysixway this worked:
```
Options +FollowSymlinks
RewriteEngine on

RewriteCond %{HTTP_HOST} ^example.com [NC]
RewriteRule ^(.*)$       http://www.example.com/ [R=301,NC]


```
However, and I feel stupid, BUT I had to enable mod_rewrite. :D

Also, if you notice in the code above I have no trailing $1 after http://www.example.com/$1 in the rewrite rule, because, and I found this out, that tells apache to use the first virtual site that you have configured, but if you leave it off then it just goes to your default site.

---

