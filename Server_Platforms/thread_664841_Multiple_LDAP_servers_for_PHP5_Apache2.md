---
title: "Multiple LDAP servers for PHP5 Apache2"
date: 2008-01-11
forum: Server Platforms
---

### Post by hangfire on 2008-01-11
I've upgraded and installed multiple LDAP Directory Servers at my site. While upgrading the Linux systems to fallover between DS's, I noticed that the (various) PHP LDAP hooks all have one Directory Server entry.

Does anyone have an example of LDAP Directory Server time-out and fail-over to backup DS within PHP5?

Thanks,
-HF

---

### Post by hangfire on 2008-01-13
bump!

---

### Post by hangfire on 2008-02-06
Bumpity Bumpity bump-bump-bump.

---

### Post by astrotech226 on 2008-02-07
I do quite a bit of LDAP with Apache and PHP.  This failover is usually automatic if the URIs are set up correctly.  Can you post an example of what you are trying to do in PHP?

It's pretty common to have the hostname portion read something like:

ldap://ldap1.yourdomain.com ldap://ldap2.yourdomain.com

If you are using ldap_connect(), it will simply switch to the backup if the first is unreachable.

---

