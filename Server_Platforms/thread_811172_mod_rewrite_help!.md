---
title: "mod_rewrite help!"
date: 2008-05-28
forum: Server Platforms
---

### Post by Dr Small on 2008-05-28
I am as dumb as a box of rocks when it comes to .htaccess and the syntax to it, and even having documentation in front of me doesn't help. I've just ever been lucky...

I am trying to setup subdomains like:
```
http://user.host.com
```

But the actual URL is:
```
http://host.com/~user
```

How would I go about getting it to work as a subdomain? I have tried the following, but I keep getting an error (see below):
```
RewriteEngine on
RewriteCond   %{HTTP_HOST}                 ^.[^.]+\.host\.com$
RewriteRule   ^(.+)                        %{HTTP_HOST}$1          [C]
RewriteRule   ^.([^.]+)\.host\.org(.*) /home/$1/public_html/$2
```

And the error:
```
Forbidden

You don't have permission to access /user.host.comuser.host.comuser.host.comuser.host.comuser.host.comuser.host.comuser.host.comuser.host.comindex.php
on this server.

Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request.
Apache/2.2 Server at mycroft.org Port 80
```

Could anyone please help me?

Dr Small

---

