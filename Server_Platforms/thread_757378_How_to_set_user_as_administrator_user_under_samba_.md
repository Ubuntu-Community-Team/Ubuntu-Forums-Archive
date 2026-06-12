---
title: "How to set user as administrator user under samba domain controller?"
date: 2008-04-16
forum: Server Platforms
---

### Post by cpthk on 2008-04-16
I realized all the user I added in samba are all regular users in windows. What if I am trying create a account that is admin account which has administrative permission when logging in from windows clients? So he can install softwares.

---

### Post by lintoolman on 2008-04-17
Here is one way, not necessarily the best way.

Create a samba account to be used as admin on the DC, or map "root" to "administrator."  This is done in the smbusers file.

Assign this account to a group and then map this group the to "Domain Admins." 

Make sure on each window box the "Domain Admins" is in the local Administrators group.  Again, this may be the default setting.

I spent many day's banging my head on this.  I would recommend reading these links.

[http://www.howtoforge.com/ubuntu-gutsy-samba-domaincontroller-p2](http://www.howtoforge.com/ubuntu-gutsy-samba-domaincontroller-p2)

[http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html](http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html)

---

