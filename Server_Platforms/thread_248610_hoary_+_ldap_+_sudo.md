---
title: "hoary + ldap + sudo?"
date: 2006-09-01
forum: Server Platforms
---

### Post by Carpe_Nox on 2006-09-01
hello all

I have to modify a few ubuntu instalations in such a way that auth information comes from LDAP. Quite a few of the clients are still running hoary...

After I modified the /etc/pam.d/common* files, I expected to be able to use sudo to elevate privileges, but that is not the case.

I searched a bit on the subject and found out tere is a package named pam-ldap for later releases of ubuntu. Is this what I need in hoary?

If not, how do I use sudo with LDAP on hoary?

Thanks

---

