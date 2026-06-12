---
title: "mod_mono does not work"
date: 2008-08-08
forum: Server Platforms
---

### Post by Pochen on 2008-08-08
Hi!
I have come some way in my path to cofigure mod_mono to work with .net and aspx-files.
But every time i tries ro reach my .aspx-file on the server the webbrowser wants to download the file instead of showing it.

Any idea what i need to change?

---

### Post by StickyStyle on 2008-08-08
not knowing anything about mod_mono, it sounds to me like apache doesnt have the mime type configured for the .aspx files.  That is done with the AddType option

[http://httpd.apache.org/docs/2.0/mod/mod_mime.html#addtype](http://httpd.apache.org/docs/2.0/mod/mod_mime.html#addtype)

You can see an example in /etc/apache2/mods-available/php5.conf

---

### Post by Pochen on 2008-08-09
i have AddType in my mod_mono.conf,but maybe that configfile is not executed? Is there a way to tell if a config-file is executed?

---

### Post by StickyStyle on 2008-08-09
is the mod_mono.conf in /etc/apache2/mods-available ? is so, have you done ```
$sudo a2enmod mod_mono
```  so it is symlink'ed in mods-enabled.

---

### Post by Pochen on 2008-08-09
hi!
yes, i have enabled it and it's symlinked.

---

