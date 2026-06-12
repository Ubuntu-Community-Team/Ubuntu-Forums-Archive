---
title: "Apache and Security"
date: 2010-06-09
forum: Security
---

### Post by brwarner on 2010-06-09
I'm new to linux and I am trying to set up security for Apache. One thing I want to do is when some page uses the "exec" PHP function it is limited to the virtual host folder's root, so they can not delete other pages from other sites hosted on the same machine.

---

### Post by bbi5291 on 2010-06-09
One possibility is to create a separate user account for each site you want to host; let the file permission system take care of the rest. The settings "User" and "Group" in apache2.conf can be overridden in the configuration files in sites-available.

---

### Post by edenCC on 2010-06-10
Also it's possible to disable some PHP's functions in php.ini, and execution path can be limited to specific path as well.

---

