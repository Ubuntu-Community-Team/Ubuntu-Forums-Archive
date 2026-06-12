---
title: "[SOLVED] Apache2 and Mozilla indexing"
date: 2008-04-02
forum: Server Platforms
---

### Post by spiderbatdad on 2008-04-02
I'm just learning how to use apache2. In the process of opening  an index.html using FireFox (locally), I clicked a link on the page to a directory in which I had not yet created an index. FireFox acted like a file browser and displayed a page shown in the screenshot below.
This would be ideal for the lazy man. Is there a directive I can use to tell apache2 to use this index in certain directories that have .htacess? That way I would not have to create another .html to display the various files therein.

---

### Post by spiderbatdad on 2008-04-03
ok. Fairly easy...
enable autoindex module: a2enmod autoindex

add directory directive Options +Indexes in the virtual host file.

RTM.

---

