---
title: "installing software and virtual hosts"
date: 2009-02-14
forum: Server Platforms
---

### Post by pdc124 on 2009-02-14
how do i install different software to each virtualhost?

eg phpmyadmin to localhost ( that I will make accessible from my LAN) and mediawiki to my external-facing hosts ?

---

### Post by hyper_ch on 2009-02-14
load it in the according virtual hosts

---

### Post by pdc124 on 2009-02-14
how ?
with apt?
or do i extract a downloaded tarball into the appropriate directory?
if so , is there any point installing it with apt-get  as well? 
or is there  a master copy that I symlink to the directories as appropriate  ?

---

### Post by hyper_ch on 2009-02-14
[http://httpd.apache.org/docs/2.0/vhosts/](http://httpd.apache.org/docs/2.0/vhosts/)

[http://httpd.apache.org/docs/2.0/mod/mod_alias.html](http://httpd.apache.org/docs/2.0/mod/mod_alias.html)

---

### Post by pdc124 on 2009-02-14
im not sure that the apache directives wiill help
eg I want
phpmyadmin, mediawiki accesible from localhost
and eg joomal and a different instance of mediawiki ( with different users, style sheets etc) in virtualhost1 and eg another instance of joomla in virtualhost 2

---

### Post by volkswagner on 2009-02-14
You will have to be careful with apt-get.  It will install to multiple directories and use certain defaults.

Either look for packages in .tar .gz or .zip and extract them to the root directory of your virtual host.  Or if you need to use apt make sure you can verify the root directory, most likely something like /var/www/mediawiki then set that as the root directory in apache virtual host config.

---

