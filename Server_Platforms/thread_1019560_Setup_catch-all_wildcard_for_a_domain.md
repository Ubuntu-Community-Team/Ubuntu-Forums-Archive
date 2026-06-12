---
title: "Setup catch-all wildcard for a domain"
date: 2008-12-23
forum: Server Platforms
---

### Post by Boffin13 on 2008-12-23
Hello.
I'm trying to setup my laptop as development machine, so I've installed LAMP server and now for one of the project I need catch-all wildcard.

I mean that all requests to *anything*.example.com will be redirected to example.com (which is on my machine and works fine).

Here is apache's config for example.com:

```

<VirtualHost *:80>
	DocumentRoot /home/boffin/example.com/
	ServerName example.com
</VirtualHost>

```

also, in my /etc/hosts I have
```

127.0.0.1 example.com

```

So, what do I need to setup catch-all wild card?

---

### Post by Titan8990 on 2008-12-23
You should check out this documentation on mod_alias:

[http://httpd.apache.org/docs/2.0/mod/mod_alias.html](http://httpd.apache.org/docs/2.0/mod/mod_alias.html)

---

