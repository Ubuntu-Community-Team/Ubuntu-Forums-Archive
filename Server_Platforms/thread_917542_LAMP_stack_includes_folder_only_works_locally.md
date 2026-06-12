---
title: "LAMP stack includes folder only works locally"
date: 2008-09-12
forum: Server Platforms
---

### Post by _nate on 2008-09-12
I am running a LAMP stack. My includes folder works locally however when I load the page on another machine on my network it says the file doesn't exist. The includes directory and file have read permissions. Any suggestions? thanks

---

### Post by azadpanchi on 2008-09-26
If you are able to connect to the apache server I would check to see if selinux is blocking you.  Look into /var/log/messages and see if you see any errors from selinux blocking you.  If so you can edit /etc/selinux/config and set it as following:
SELINUX=disabled

If you want to configure selinux instead of disabling you can refer to documentation on the web, like [www.engardelinux.org/doc/guides/selinux-quick-start-guide/selinux-quick-](www.engardelinux.org/doc/guides/selinux-quick-start-guide/selinux-quick-) start-guide.pdf

---

