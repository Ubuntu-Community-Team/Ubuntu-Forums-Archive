---
title: "apache2 ubuntu"
date: 2013-09-28
forum: Server Platforms
---

### Post by remo2 on 2013-09-28
Whats definition of 000-default.conf file?

---

### Post by Lars Noodén on 2013-09-28
Your machine can host many different web sites, even with different addresses.  Each web site is defined by its own configuration file.  000-default is a sample configuration to get you started with a single [virtual host](http://httpd.apache.org/docs/2.4/vhosts/).  Is that what you were wondering?

If you were to have a second web site on the same machine, you would just add a second configuration file pointing to a second DocumentRoot where the other web pages would be stored.

---

### Post by remo2 on 2013-09-28
yes

---

