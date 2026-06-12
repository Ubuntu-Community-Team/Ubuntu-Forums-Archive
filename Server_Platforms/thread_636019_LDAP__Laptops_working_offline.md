---
title: "LDAP : Laptops working offline"
date: 2007-12-09
forum: Server Platforms
---

### Post by delerious010 on 2007-12-09
A Win2k+ box connects to network and caches it's domain credentials. These credentials are then available when working offline.

What is the LDAP \ NSS \ PAM equivalent of this ? 

Thanks.

---

### Post by gpredrag on 2007-12-09
Those would be pam_ccreds that caches successful authentication, and nss_updatedb with pam_db that makes off line copy of LDAP database for nsswitch,

---

