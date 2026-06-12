---
title: "Xen 4.2 - Migration"
date: 2013-02-26
forum: Virtualisation
---

### Post by fredboo on 2013-02-26
Hi all, 

I recently upgrated Xen 4.1 to Xen 4.2.1.

I [read]("http://wiki.xen.org/wiki/XEND") that the daemon configuration file etc/xen/xend-config.sxp has been deprecated. 
 
Indeed, I opened it and all the security options for live migration are commented [#(enable-ssl-server no)], so i consider that it's enable by default. (?)

- is there any other configuration file considering security in live migration?

- if not, from where i can adjust the security settings? is it a valid option to modify the xend-config.sxp or is useless now?

thanks

---

