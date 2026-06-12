---
title: "mod_rewrite in userdirs causing funny errors"
date: 2008-02-24
forum: Server Platforms
---

### Post by pedrotuga on 2008-02-24
I am trying to use mod_rewrite in my ~/public_html
But for some reason it's rewriting the urls to the server web root instead

I used this method to test it

[http://www.wallpaperama.com/forums/how-to-test-check-if-mod-rewrite-is-enabled-t40.html](http://www.wallpaperama.com/forums/how-to-test-check-if-mod-rewrite-is-enabled-t40.html)

When i try the rewritten url I get a 404.

Here's the error log
```

[Sun Feb 24 22:23:15 2008] [error] [client 127.0.0.1] File does not exist: /var/www/home, referer: http://localhost/~p/rewrite.php?link=1

```

Is there anything I need to be aware of when using mod rewrite in userdirs?

---

### Post by rapiscan on 2008-02-25
Hello,

It would be helpful if you posted your .htaccess file.  

Also make sure that mod_rewrite is installed and enabled (just a precaution).

---

### Post by pedrotuga on 2008-02-25
rewrite is enable and working. I checked that before

The link I posted has the htaccess I am using.
Anyway, fr clearness here it goes:

```

RewriteEngine On
RewriteRule ^link([^/]*)\.html$ rewrite.php?link=$1 [L]
```

---

### Post by rapiscan on 2008-02-25
Does this link work when you go to it directly?
[http://localhost/~p/rewrite.php?link=1](http://localhost/~p/rewrite.php?link=1)

My initial guess is that something fishy is going on witht he per-user directory.  The URL [http://localhost/~p/](http://localhost/~p/) should go to the user directory, which is usually /var/home/username/public_html/

It seems that apache is checking /var/www/home/ instead, which doesn't exist. I would check out the apache config to make sure that the user dir options are all correct.

[http://httpd.apache.org/docs/2.0/howto/public_html.html](http://httpd.apache.org/docs/2.0/howto/public_html.html)

---

### Post by pedrotuga on 2008-02-25
the userdirs are working without trouble, I am developing a php aplication in m userdir, the troubles only started when I wanted to use mod_rewrite

---

