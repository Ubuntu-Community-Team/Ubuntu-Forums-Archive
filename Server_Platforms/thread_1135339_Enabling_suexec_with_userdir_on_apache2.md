---
title: "Enabling suexec with userdir on apache2"
date: 2009-04-24
forum: Server Platforms
---

### Post by shagymoe on 2009-04-24
Hi all,

I need to enable suexec with userdir on Hardy.  I have apache installed and enabled suexec with a2enmod, but it seems that to use suexec with userdir, you have to compile with the "--with-suexec-userdir=DIR" option.

Is there are way to enable this without compiling or another way to get this working?

Thanks a lot.

---

### Post by rrll1977 on 2009-05-18
Hi,

Have you got to work mod_rewrite with mod_userdir

I can't get mod_rewrite to work with user's pages on /home/user/public_html, although it appears to work fine for server root pages on /opt/lampp/htdocs

Regards

---

