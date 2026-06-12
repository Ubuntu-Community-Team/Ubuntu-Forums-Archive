---
title: "LDAP + Kerberos Heimdal"
date: 2008-07-21
forum: Server Platforms
---

### Post by delerious010 on 2008-07-21
I'm looking to setup Kerberos with an LDAP backend on Hardy.
Would anyone happen to have a well rounded how-to 

I've followed a few so far, and there always seems to be parts missing. For instance, I've not found many details on the LDAP entries that need to be created. 

So currently, I can get tokens from the KDC via kinit/klist, however trying to execute kadmin and specifying the principal name gives me : "kadmin: kadm5_init_with_password: No KDC found for realm".

My config files seem ok, I'm thinking it may be due to there being no krb5Realm instance in my LDAP. *shrug*.

Anyways any help, ideas, tips, tricks, etc... would be appreciated.

---

