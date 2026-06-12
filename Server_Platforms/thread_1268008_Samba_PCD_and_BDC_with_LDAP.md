---
title: "Samba PCD and BDC with LDAP"
date: 2009-09-16
forum: Server Platforms
---

### Post by x2r on 2009-09-16
Hi,

I’m trying to implement project whit 2 servers. One Samba PCD whit LDAP (master) server and the second Samba BDC with LDAP (slave). At the moment i have the PDC server working (LDAP and Samba). I have about 50 users woking in Windows XP and they have rooming profiles. My problem is how i configure the BDC server and LDAP slave. 

The main idea is, if i have some problem with PDC server the BDC server take control.  How can i do it?

Any help will be appreciated.

Thanks

Ron

---

### Post by ainsworth_t on 2009-09-16
See if this helps: [http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-bdc.html](http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-bdc.html)

---

