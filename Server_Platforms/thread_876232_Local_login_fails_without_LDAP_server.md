---
title: "Local login fails without LDAP server"
date: 2008-07-31
forum: Server Platforms
---

### Post by dodeantn on 2008-07-31
Hi,

I hope you can help me with the following problem.

I've got a network configuration, where the users are authenticated an supported by a combination of LDAP, Samba and NFS (= PDC = primary domain controller).

As long as the server runs (and with it LDAP, Samba and NFS) everything is OK an works perfectly.

On all computers, no matter if server or client, there is a admin-account set up (uid: ubuntu). This account is available only locally (= /etc/passwd, /etc/shadow) and it's not in the LDAP directory, since it would cause trouble with the [u|g]id's and the home directories. -- "ubuntu" is a local admin, who survives no matter if the net or the server is down.

Now: if the server is down, this local admin account won't work anymore. It takes an age until anything happens. When something happens, it's an error message saying: "Failed to initialize HAL."

I've already googled, searched in forums, in bug-trackers -- nothing.

I've tried changing pam.d config ("compat ldap" -> "files ldap") -- nothing; setting timeouts (LDAP, DNS) -- nothing.

Many thanks in advance,

Cheers

---

### Post by kcnnc on 2008-10-09
Any solution to this issue yet?

---

