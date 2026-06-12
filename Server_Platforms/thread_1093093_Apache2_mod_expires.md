---
title: "Apache2 mod_expires"
date: 2009-03-11
forum: Server Platforms
---

### Post by mjrmua on 2009-03-11
I'm trying to enable mod_expires on my ubuntu web server, to allow caching of my webpages on client browsers.

I've added:
```

<IfModule mod_expires.c>
  ExpiresActive On
  ExpiresDefault "access plus 1 hour"
</IfModule>

```
to /etc/apache2/mods-available/expires.conf

and run
```

sudo a2enmod headers
sudo a2enmod expires
sudo /etc/init.d/apache2 restart

```

But my HTTP headers still have no "Expires" tag.  What's the secret to getting this working?

---

### Post by mjrmua on 2009-03-11
:oops: My mistake, Problem was caching disabled on firefox, not anything wrong with apache.

Sending firefox to about:config revealed browser.cache.disk.enable and browser.cache.memory.enable both set as false.  Have changed these and caching working nicely.

---

