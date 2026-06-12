---
title: "Apache2, PHP5 : a2enmod|grep php == &quot;&quot;"
date: 2006-03-20
forum: Server Platforms
---

### Post by Burke on 2006-03-20
I have the following installed:

apache2
php5
libapache2-mod-php5

...and whichever other packages were required along the way. Now here's the catch. The PHP5 module is apparently unavailable to Apache, and when I load a *.php in my browser, it tries to download it (file of type: PHTML)
```

root@burke:/etc/apache2 # a2enmod
Which module would you like to enable?
Your choices are: actions asis auth_anon auth_dbm auth_digest auth_ldap cache cern_meta cgid cgi dav_fs dav deflate disk_cache expires ext_filter file_cache headers imap include info ldap mem_cache mime_magic proxy_connect proxy_ftp proxy_http proxy rewrite speling ssl suexec unique_id userdir usertrack vhost_alias
Module name? ___
```

No PHP. What gives? It should be there because I have libapache2-mod-php5, right? I did "/etc/init.d/apache2 restart", several times even, and no changes.

Here's ls /etc/apache2/mods-available | grep php:
```



```

Yeah, it's blank.

I tried uncommenting the line to add x/application-httpd-php (or whatever it is) in /etc/apache2/apache2.conf, and still no go (yes, I restarted).

Any ideas, anyone?

---

### Post by MJN on 2006-03-20
Installing libapache2-mod-php5 should indeed have installed the module, might be worth reinstalling libapache2-mod-php5?

Mathew

---

### Post by Burke on 2006-03-20
I've actually tried that already. I'll try doing a complete removal and reinstall, and edit this with the results.
[B]
EDIT: Ah! That did indeed fix the problem. I purged, then installed libapache2-mod-php5. Thank you very much, MJN.[/B]

---

### Post by MJN on 2006-03-20
I can't really take any credit... it was a bit of a Windows-esque type of suggestion (i.e. if it's bust, start again!) ;)

Mathew

---

