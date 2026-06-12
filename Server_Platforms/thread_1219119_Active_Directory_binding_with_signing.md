---
title: "Active Directory binding with signing"
date: 2009-07-21
forum: Server Platforms
---

### Post by shizakapayou on 2009-07-21
I run an Ubuntu Server 8.04.3 64-bit system on my domain, the domain controller is Windows Server 2008.  On the domain controller, I'm getting reports of clients performing SASL LDAP binds without requesting signing.  Looking at the logs further, the Ubuntu server appears to be the culprit.

I'd like to bump the security around here up a bit by rejecting these binds, but obviously I need to figure out how to configure the server for this.  I will likely also have a few Ubuntu desktops joined to the domain eventually, so this would be useful then as well.

The server was joined to the domain using the following:

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)
[https://help.ubuntu.com/community/Samba/Kerberos](https://help.ubuntu.com/community/Samba/Kerberos)

Has anyone around here done this?

---

### Post by shizakapayou on 2009-07-23
Anyone?

---

