---
title: "multiple virtual hosts, http and https"
date: 2010-09-15
forum: Server Platforms
---

### Post by divided on 2010-09-15
What is the best way to go about setting up multiple virtual hosts on the same box, one using http and one using https/ssl?  I'd like to serve them from the same ip address if possible; I know it's possible in apache 1.3.

Any help is greatly appreciated.  Thanks in advance.

---

### Post by divided on 2010-09-16
Anyone have any suggestions?

---

### Post by terazen on 2010-09-16
[http://httpd.apache.org/docs/current/mod/core.html#namevirtualhost](http://httpd.apache.org/docs/current/mod/core.html#namevirtualhost)

You add multiple sites in /etc/apache2/sites-available, run "sudo a2ensite sitename", and restart apache.  The "a2ensite" thing just adds a link in /etc/apache2/sites-enabled.

---

