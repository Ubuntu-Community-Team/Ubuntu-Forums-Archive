---
title: "Freeradius not starting."
date: 2011-03-05
forum: Server Platforms
---

### Post by headvampyre@hotmail.co.uk on 2011-03-05
Hi, im running Freeradius in a CHROOT environment for Samba4 and im having issues starting it when its CHROOTED. Basically, i get an error about the 'rlm_ldap' module, but i know its there (/CHROOTDIR/usr/lib/freeradius/rlm_ldap). My logs only show that it cant find the file. Heres my log:

Sat Mar  5 15:53:02 2011 : Error: /etc/freeradius/modules/ldap[1]: Failed to link to module 'rlm_ldap': file not found 
Sat Mar  5 15:53:02 2011 : Error: /etc/freeradius/sites-enabled/default[23]: Failed to load module "ldap".
Sat Mar  5 15:53:02 2011 : Error: /etc/freeradius/sites-enabled/default[23]: Failed to parse "ldap" entry.
Sat Mar  5 15:53:02 2011 : Error: Failed to load virtual server <default>

Will appreciate any help in this :) Thanks in advance.

---

