---
title: "Problem configuring samba and ldap"
date: 2009-01-05
forum: Server Platforms
---

### Post by erfaan on 2009-01-05
Hi,
I just installed ubuntu 8.10 server. I am trying to use it as PDC. I followed this guide:

[https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html]("https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html")

Everything is working perfectly alright except that I cannot configure my windows XP to use this domain. Problem is that whenever I try to add my windows xp to this domain, samba server crashes. I get the following error in my samba log:

```

[2009/01/05 14:19:28,  0] lib/smbldap.c:smb_ldap_start_tls(596)
  Failed to issue the StartTLS instruction: Protocol error
[2009/01/05 14:19:28,  1] lib/smbldap.c:another_ldap_try(1178)
  Connection to LDAP server failed for the 1 try!

```

Here is my smb.conf file:

```

   passdb backend = ldap:ldap://server
   ldap suffix = dc=server
   ldap user suffix = ou=People
   ldap group suffix = ou=Groups
   ldap machine suffix = ou=Computers
   ldap idmap suffix = dc=server
   ldap ssl = no
   ldap admin dn = cn=admin,dc=server
   ldap passwd sync = yes

   add machine script = sudo /usr/sbin/smbldap-useradd -t 0 -w "%u"

```

Can anyone help me please?

---

### Post by mspisars on 2009-01-21
Looks to me like your configuration is using the TLS transport mode, and it is probably not configured right. I would start by not using the TLS transport and see if you can get it working that way first then you can go on to trying to configure TLS.

A link for reference: [http://www.iallanis.info/smbldap-tools/docs/samba-ldap-howto/#htoc35](http://www.iallanis.info/smbldap-tools/docs/samba-ldap-howto/#htoc35)

---

