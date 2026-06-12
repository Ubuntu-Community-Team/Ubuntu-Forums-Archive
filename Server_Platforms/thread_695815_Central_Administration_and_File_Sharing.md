---
title: "Central Administration and File Sharing"
date: 2008-02-13
forum: Server Platforms
---

### Post by arcoMarco on 2008-02-13
Hi,

I'd like to built a linux only test network with some clients and a server.
In a Windows environment I know there is Active Directory for central administer user's and client's permissions and to deploy software & policy for the domain.
In a linux environment what kind of tool can replace all the features of an AD environment?
Can ldap deploy policy or software?

Also, if I want enable file sharing for linux machines, should I use samba or for a linux only network is there something else?

Thank you,

Marco

---

### Post by crouton on 2008-02-13
Active Directory is an extended/modified version of LDAP; part of those modifications are the policies you mentioned.  Vanilla LDAP is your basic organizational directory.  That said, there may be other LDAP programs/extensions that emulate Active Directory's feature-set but I don't know of any off-hand.

NFS is the usual means of file-sharing on a Linux-centric network.  If you ever intend to bring other OS's into the mix (Windows, Mac, etc) you might want to stick with Samba.

---

### Post by arcoMarco on 2008-02-14
> **crouton said:**
> Active Directory is an extended/modified version of LDAP; part of those modifications are the policies you mentioned.  Vanilla LDAP is your basic organizational directory.  That said, there may be other LDAP programs/extensions that emulate Active Directory's feature-set but I don't know of any off-hand.



Thank you for your reply.
I don't want something that emulate AD but something that allow me to administer centrally many clients for updates, policies and so on..
Any ideas?

Thank you

Marco

---

### Post by crouton on 2008-02-14
I don't know of any Linux-oriented programs that do what you are requesting but I've never had to use such programs (yet.)  Policies may be your biggest stumbling block; I know that Samba3 can currently emulate most things in a NT-4-style domain, and Samba4 (still in alpha testing) is planned to have full ActiveDirectory compatability.

---

