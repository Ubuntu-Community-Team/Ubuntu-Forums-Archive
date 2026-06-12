---
title: "Making mediawiki the root document?"
date: 2006-06-20
forum: Server Platforms
---

### Post by thk on 2006-06-20
Anyone know how to make mediawiki come up by default rather than having to type /mediawiki? I've tried symlinking /var/lib/mediawiki/index.php to /var/www, but that does not work. I've tried Alias / /mediawiki, but that causes problems. I've tried Redirect ^/$ /mediawiki -- no luck there. I've tried .htaccess files. This ought to be simple.

---

### Post by jstueve on 2006-06-20
I've done it using .htaccess.  What did you try in .htaccess and is httpd.conf (or similar apache2.conf) allowing .htaccess to do rewrites? (AllowOverrides ?)

---

### Post by thk on 2006-06-20
That's probably what I did wrong -- I must need a Directory entry in the apache config to allow overrides. I'll try again and post something. Did you use a Redirect in the .htaccess file?

---

### Post by thk on 2006-06-20
Finally got it by putting

```
RedirectMatch ^/$ http://host/mediawiki/

```
in /etc/apache2/apache2.conf. I've no idea why
```

RewriteRule ^/$ /mediawiki/ [R] 
```

does not work.

---

