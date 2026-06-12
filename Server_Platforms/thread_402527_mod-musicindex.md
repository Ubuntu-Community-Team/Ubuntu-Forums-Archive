---
title: "mod-musicindex"
date: 2007-04-05
forum: Server Platforms
---

### Post by mzracer360 on 2007-04-05
I installed and configured mod-musicindex for apache2.  It works perfectly, but I would like to know how to modify the look of the webpage.

---

### Post by mzracer360 on 2007-04-07
Bump.

Anyone know?

---

### Post by rasmusfromdenmark on 2007-09-01
Late reply, but never the less :-)

The installation does not create a link to /usr/share/mod_musicindex/ 

This is done by:

ln -s /usr/share/mod_musicindex/ /var/www/musicindex/

This will put some style to your web pages. This css file can also be adjusted, at least to some extend.

/rasmus

---

