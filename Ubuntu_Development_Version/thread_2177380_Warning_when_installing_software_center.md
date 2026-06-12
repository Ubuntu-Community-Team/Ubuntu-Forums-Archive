---
title: "Warning when installing software center"
date: 2013-09-28
forum: Ubuntu Development Version
---

### Post by Ramesh_Jude_Fernando on 2013-09-28
Hi all, I got this warning when running apt-get install upgrade on Saucy 13.10
Setting up software-center (13.09-0ubuntu1) ...
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser-layer.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application

Anyone, know why?

---

### Post by wgarcia on 2013-09-28
See:

[https://bugs.launchpad.net/ubuntu/+source/app-install-data-ubuntu/+bug/1161283](https://bugs.launchpad.net/ubuntu/+source/app-install-data-ubuntu/+bug/1161283)

if you want to add yourself to that report.

---

### Post by rrnbtter on 2013-09-28
Greetings,
We were getting software center warnings on specific applications during the Raring Dev also. This looks like more of the same. It has been reported.

---

