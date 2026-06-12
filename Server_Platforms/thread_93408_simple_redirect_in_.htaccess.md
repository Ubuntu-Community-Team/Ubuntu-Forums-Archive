---
title: "simple redirect in .htaccess"
date: 2005-11-21
forum: Server Platforms
---

### Post by OneSeventeen on 2005-11-21
I need to redirect:
foo.example.com
to
[www.example.com/~foo/](www.example.com/~foo/)

reguardless of what is behind foo.example.com....
so:
foo.example.com
foo.example.com/bar
foo.example.com/bar/baz.htm

all get redirected to:

[www.example.com/~foo/](www.example.com/~foo/)

**But....**
I want
foo.example.com/baz
foo.example.com/baz/quz
etc.
to be redirected to
[www.example.com/~bazsite](www.example.com/~bazsite)

Does that make sense?

---

### Post by oskude on 2005-11-22
never done that,
try google with "htaccess subdomain"

---

### Post by chipmonk010 on 2005-11-22
check out [www.zoneedit.com](www.zoneedit.com), you can use this to manage dns redirects from foo.example.com to whereever. i use it and it works quite nicely

---

### Post by OneSeventeen on 2005-11-22
Okay, apparently the .htaccess things I was trying were good, but my apache2 configuration was bad, so now that I have .htaccess working and mod_rewrite working:

Assume this file is on a server that has 2 subdomains: foo and foodev
```
RewriteEngine on
#first filter out all foodev.example.com requests:
RewriteCond %{HTTP_HOST} !^foodev.example.com$

#now filter out all requests from the IP 111.222.333.444:
RewriteCond %{REMOTE_ADDR} !^111\.222\.333\.444

#now filter out all requests for foo.example.com/bar :
RewriteCond %{REQUEST_URI} !^/bar

#now rewrite the URL based on the above restrictions:
RewriteRule (.*) http://www.example.com/~foo/ [R,L]

#once again filter otu foodev.example.com requests:
RewriteCond %{HTTP_HOST} !^foodev.example.com$

#and still filter out the chosen static IP
RewriteCond %{REMOTE_ADDR} !^111\.222\.333\.444

#now redirect the user!
RewriteRule (.*) http://www.example.com/~barsite/ [R,L]

```

So what this does is redirects:
foo.example.com/and/anything/else
to
www.example.com/~foo/

*BUT*
It catches foo.example.com/bar/and/anything/else
and redirects those to:
www.example.com/~barsite

*And:*
It doesn't do anything if it is coming from the IP 111.222.333.444  (which I set to my static IP)
And it also won't do anything if I request foodev.example.com, but I need to get that subdomain pointed at the server before that works.

viola!

---

