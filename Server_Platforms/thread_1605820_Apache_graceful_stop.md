---
title: "Apache graceful stop?"
date: 2010-10-25
forum: Server Platforms
---

### Post by 448191 on 2010-10-25
I can do sudo $ service apache2 graceful and it'll do a graceful restart, but looking at /etc/init.d/apache2, the only way I can do a graceful shutdown is is running $ /usr/sbin/apache2ctl -k graceful-stop

But that results in a PID error: httpd (pid xxxxx?) not running

Obviously Ubuntu/Debian does not mean for me to run this command directly.

Basically wat I'd like to do is do a graceful shutdown (as in wait for requests to complete), perform my upgrades, and start the server again.

Suggestions?

---

### Post by 448191 on 2010-10-26
Bump?

---

### Post by 448191 on 2010-10-27
Bump.

---

