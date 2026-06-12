---
title: "mod_chroot + apache2 = FAIL?"
date: 2010-02-21
forum: Server Platforms
---

### Post by deltatux on 2010-02-21
Hey guys,

This is really really annoying me. I need to chroot my Apache 2 install but it just won't work. If I turn off Apache 2's mod_chroot then it works.

This is the error:
> 
[notice] mod_chroot: changed root to /chroot/httpd.
[alert] (2)No such file or directory: Can't chdir to /chroot/httpd


The documentroot is set to /var/www so I mounted /var/www to /chroot/httpd/var/www.

I also mounted /home to /chroot/httpd/home and /etc/passwd to /chroot/httpd/etc/passwd.

However, here's my directory listing for /chroot/httpd:
[img]http://img14.imageshack.us/img14/3559/chroothttpddir.png[/img]


Thanks,
deltatux

---

### Post by benhauer on 2010-02-24
Hi,

Can we please see your complete, unedited config file?

regards,
-- 
Marek

---

