---
title: "Error 403 on files copied into /var/www"
date: 2010-03-29
forum: Server Platforms
---

### Post by nightmicu on 2010-03-29
Hi everyone,

  Installed LAMP (Apache2, MySQL, PHP) and everything is working fine. However, when I copied & pasted a folder from my Windows partition into /var/www, I receive an Error 403 - Forbidden when I try to navigate to those pages/files. They were moved into the folder using gksudo nautilus.

Ideas??? Trying to continue working on a website locally in Ubuntu that was started in Vista.

Thanks!

---

### Post by nightmicu on 2010-03-29
Figured it out, had to change permissions to "Access" for all folders that I copied.. yay me! :)

---

