---
title: "Enable localhost/~username addresses"
date: 2007-04-25
forum: Server Platforms
---

### Post by neko18 on 2007-04-25
I installed apache and can access [http://localhost/](http://localhost/) but not [http://localhost/~my_username/](http://localhost/~my_username/) but it gives me a 404. I have a ~/public_html/ directory and an index.html file in there, but I still get a 404. I'm using Ubuntu 7.04 (Desktop) and installed the package apache2.

Any suggestions?
Thanks

---

### Post by strixy on 2007-04-26
Check your /etc/apache2/mods_enabled directory for mod_public_html.load

If that mods not plugged in and enabled, it won't work. 

Reference material,

[http://httpd.apache.org/docs/2.2/howto/public_html.html](http://httpd.apache.org/docs/2.2/howto/public_html.html)

tip: It's included by default, but not turned on. You'll have to copy it from /etc/apache2/modsavailable to ../modsenabled and then restart apache. (sudo apache2 -k restart).

---

### Post by llamakc on 2007-04-26
Or you could enable it with `sudo a2enmod userdir` and restart apache2.

---

### Post by strixy on 2007-04-26
uh yeah... what he said! \\:D/

---

### Post by neko18 on 2007-04-26
`sudo a2enmod userdir` worked great, thanks!

---

