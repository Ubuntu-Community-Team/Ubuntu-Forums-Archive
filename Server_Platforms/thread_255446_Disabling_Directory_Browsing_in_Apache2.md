---
title: "Disabling Directory Browsing in Apache2"
date: 2006-09-11
forum: Server Platforms
---

### Post by fsgpr on 2006-09-11
I have an Apache2 server setup using Mod_Python with Ubuntu 6.06 and would like to know how to disable directory browsing.

I already tried deleting "Indexes" from the /etc/apache2/apache2.conf file as I found on Google and restarting Apache2 (sudo apache2 -k restart), but I can still browse through directories...

Anything else that needs to be modified?

---

### Post by kidders on 2006-09-11
Hi there,

There may be other places you need to remove that directive from ... it really depends on how your apache is configured. Try searching your apache config files (there are quite a few!) for other occurrences of the "indexes" directive that might apply to your directory.

---

### Post by fsgpr on 2006-09-11
Thanks for the pointer.

It turned out to be in /etc/apache2/sites-available/default

---

### Post by kidders on 2006-09-11
Great news :-)

Those individual site settings override any default ones you specify elsewhere. Of course, a .htaccess file can, in turn, override those.

Best of luck!

---

### Post by ruthgard on 2008-07-17
I noticed that it did not help to just remove the Indexes word from the configuration. I allso had to add the global(ie not wrapped in any other configuration block as Directory or such) option:

```
Option -Indexes
```

to the /etc/apache2/apache2.conf and then restart apache. Now I get the forbidden message when I try to access a folder, just as I wanted it to.

---

