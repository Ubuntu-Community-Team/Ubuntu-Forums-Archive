---
title: "How to enable WebDAV"
date: 2008-12-12
forum: Server Platforms
---

### Post by divinequran on 2008-12-12
i want other to access my machine through apache as a shared system in the network can this be done using WebDAV in apache if so then How to enable WebDAV module in my apache.

---

### Post by Wayne_V on 2008-12-12
I'm not sure if I understand completely what you want to do but maybe you could start by looking at the davfs2 package:

$ apt-cache show davfs2

[http://dav.sourceforge.net/](http://dav.sourceforge.net/)

---

### Post by Wayne_V on 2008-12-12
for webdav on apache, see this page:  [http://httpd.apache.org/docs/2.0/mod/mod_dav.html](http://httpd.apache.org/docs/2.0/mod/mod_dav.html)

Ubuntu uses the a2enmod - just run a2enmod to see a list of modules available.

---

### Post by divinequran on 2008-12-16
Thanks for your reply i got some ides from the provided link.

---

