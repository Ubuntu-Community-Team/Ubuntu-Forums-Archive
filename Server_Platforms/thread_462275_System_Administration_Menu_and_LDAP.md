---
title: "System Administration Menu and LDAP"
date: 2007-06-02
forum: Server Platforms
---

### Post by garethbult on 2007-06-02
Hi,

I've now successfully rolled out libnss-ldap and libpam-ldap and people can happily log in via GDM and run off the automounter etc etc.

However, try as I might, I can't get the System -> Administration user to appear for Admins .. at least not all the entries. 

I've made sure users are in the "admin" group - this doesn't work.
I've tried adding specific users to the sudoers file - this also has no effect.

So it seems that once a user become an LDAP user, they no longer have the ability to be a local admin ??

Is there any way to change this ??
What mechanism controls the appearance of 'restricted' entries in the system admim menu ?
(I'm using 7.04)

tia
Gareth.

---

