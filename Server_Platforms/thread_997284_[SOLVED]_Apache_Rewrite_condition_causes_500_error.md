---
title: "[SOLVED] Apache: Rewrite condition causes 500 errors on 404"
date: 2008-11-29
forum: Server Platforms
---

### Post by tubezninja on 2008-11-29
This may be more an apache thing than an ubuntu thing, but I figured this might be a good place to start....

I have an ubuntu 8.04 LTS 64-bit server, running the standard LAMP package, and AllowOverride On so that users can have .htaccess files.  I have a user with the following in their .htaccess:

```
# Allows .py files to be pulled from Apache without a .py extension
# I.E /about instead of /about.py
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ $1.py [L,QSA]

```

As stated in the commented lines, this little snippet is intended to python scripts to run without having a .py extension.

I suspect this is causing the Apache server to throw a 500 Internal Server error when a user enters an invalid URL (and thus should be giving a 404 Not Found).  The logs, in debug mode, show this whenever an invalid URL is encountered (in this case "http://servername.com/thiswill404_lawlz"):


```

$ tail error.log
[Sat Nov 29 22:30:55 2008] [debug] core.c(3052): [client 72.88.145.105] redirected from r->uri = /thiswill404_lawlz.py.py.py.py.py.py.py.py
[Sat Nov 29 22:30:55 2008] [debug] core.c(3052): [client 72.88.145.105] redirected from r->uri = /thiswill404_lawlz.py.py.py.py.py.py.py
[Sat Nov 29 22:30:55 2008] [debug] core.c(3052): [client 72.88.145.105] redirected from r->uri = /thiswill404_lawlz.py.py.py.py.py.py
[Sat Nov 29 22:30:55 2008] [debug] core.c(3052): [client 72.88.145.105] redirected from r->uri = /thiswill404_lawlz.py.py.py.py.py
[Sat Nov 29 22:30:55 2008] [debug] core.c(3052): [client 72.88.145.105] redirected from r->uri = /thiswill404_lawlz.py.py.py.py
[Sat Nov 29 22:30:55 2008] [debug] core.c(3052): [client 72.88.145.105] redirected from r->uri = /thiswill404_lawlz.py.py.py
[Sat Nov 29 22:30:55 2008] [debug] core.c(3052): [client 72.88.145.105] redirected from r->uri = /thiswill404_lawlz.py.py
[Sat Nov 29 22:30:55 2008] [debug] core.c(3052): [client 72.88.145.105] redirected from r->uri = /thiswill404_lawlz.py
[Sat Nov 29 22:30:55 2008] [debug] core.c(3052): [client 72.88.145.105] redirected from r->uri = /thiswill404_lawlz
[Sat Nov 29 22:30:55 2008] [debug] mod_deflate.c(619): [client 72.88.145.105] Zlib: Compressed 711 to 441 : URL /thiswill404_lawlz.py.py.py.py.py.py.py.py.py.py
```

It looks like Apache is recursively adding .py's to every invalid URL, until it hits the maximum number of internal redirects and gives up, throwing a 500.

Does anyone know of a way to allow us to, uhm, have our cake and eat it, too?  In other words, how can we run python scripts lacking a .py extension, without Apache continually adding a another .py to every invalid URL?

thanks for any help!

---

### Post by terazen on 2008-11-30
I'd have to rebuild my testbox to try these, but I googled a couple things maybe you could try if you haven't already.  Basically I'd try to do something with .py.py or .py.py.py requests so it never makes it past 2 or 3 rewrite attempts.

According to [http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html](http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html) this might be easiest.  It's supposed to give a 403 error for filename.py.py.

RewriteRule  .*.py.py$   - [F]

Also you could maybe try setting LimitInternalRecursion to lower number or blocking access to files with the apache config.
<Files ~ "\.py.py.py$">
Order allow,deny
Deny from all
</Files>

Maybe this helps.

---

### Post by tubezninja on 2008-11-30
Thank you for the info on this.  What I would really prefer though, is if we could get Apache to simply stop and return a 404 after the first (or second or third) time that that .py iterations fail to produce a file, since that's really what's going on here.  We had though that the L in "RewriteRule ^(.*)$ $1.py [L,QSA]" would have done the trick, but that doesnt' seem to be the case.

---

### Post by MJN on 2008-11-30
You need a conditional statement that ensures the rewrite does not get performed if the request already contains a .py extension.

As things currently stand your request for thiswill404_lawlz matches because it doesn't exist (as a file/directory) and so gets rewritten as thiswill404_lawlz.py. This new request also matches because it doesn't exist (as a file/directory) and so gets rewritten as thiswill404_lawlz.py.py. And so on...

You need to interrupt this endless loop by stopping at the first .py rewrite and then letting the requested file fail as a non-existent file. The following should do it:

```

# Allows .py files to be pulled from Apache without a .py extension
# I.E /about instead of /about.py
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_FILENAME} !^.*\.py$
RewriteRule ^(.*)$ $1.py [L,QSA]
```Mathew

---

### Post by tubezninja on 2008-11-30
It works!  Thanks so much! :)

---

