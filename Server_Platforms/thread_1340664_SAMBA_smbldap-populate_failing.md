---
title: "SAMBA: smbldap-populate failing"
date: 2009-11-28
forum: Server Platforms
---

### Post by vonjoost on 2009-11-28
Hi All,

I've been following some of the guides around the ubuntu forums on how to get samba to work with OpenLDAP.  I'm almost done but I can't get past this one stage (there were plenty of hitches along the way... I just can't seem to tackle this one).

```

Populating LDAP directory for domain EXOFFICE (S-1-5-21-4252161081-1443524649-2898400037)
(using builtin directory structure)

entry dc=example,dc=office already exist. 
adding new entry: ou=people,dc=example,dc=office,dc=example,dc=office
failed to add entry: No such object at /usr/sbin/smbldap-populate line 499, <GEN1> line 12.
adding new entry: ou=groups,dc=example,dc=office,dc=example,dc=office
failed to add entry: No such object at /usr/sbin/smbldap-populate line 499, <GEN1> line 17.
adding new entry: ou=people,dc=example,dc=office,dc=example,dc=office
failed to add entry: No such object at /usr/sbin/smbldap-populate line 499, <GEN1> line 22.
adding new entry: ou=Idmap,dc=example,dc=office,dc=example,dc=office
failed to add entry: No such object at /usr/sbin/smbldap-populate line 499, <GEN1> line 27.
adding new entry: uid=root,ou=people,dc=example,dc=office,dc=example,dc=office
failed to add entry: No such object at /usr/sbin/smbldap-populate line 499, <GEN1> line 58.
adding new entry: uid=nobody,ou=people,dc=example,dc=office,dc=example,dc=office
failed to add entry: No such object at /usr/sbin/smbldap-populate line 499, <GEN1> line 89.
adding new entry: cn=Domain Admins,ou=groups,dc=example,dc=office,dc=example,dc=office
failed to add entry: No such object at /usr/sbin/smbldap-populate line 499, <GEN1> line 101.
adding new entry: cn=Domain Users,ou=groups,dc=example,dc=office,dc=example,dc=office
failed to add entry: No such object at /usr/sbin/smbldap-populate line 499, <GEN1> line 112.
adding new entry: cn=Domain Guests,ou=groups,dc=example,dc=office,dc=example,dc=office
failed to add entry: No such object at /usr/sbin/smbldap-populate line 499, <GEN1> line 123.
adding new entry: cn=Domain Computers,ou=groups,dc=example,dc=office,dc=example,dc=office
failed to add entry: No such object at /usr/sbin/smbldap-populate line 499, <GEN1> line 134.
adding new entry: cn=Administrators,ou=groups,dc=example,dc=office,dc=example,dc=office
failed to add entry: No such object at /usr/sbin/smbldap-populate line 499, <GEN1> line 179.
adding new entry: cn=Account Operators,ou=groups,dc=example,dc=office,dc=example,dc=office
failed to add entry: No such object at /usr/sbin/smbldap-populate line 499, <GEN1> line 201.
adding new entry: cn=Print Operators,ou=groups,dc=example,dc=office,dc=example,dc=office
failed to add entry: No such object at /usr/sbin/smbldap-populate line 499, <GEN1> line 212.
adding new entry: cn=Backup Operators,ou=groups,dc=example,dc=office,dc=example,dc=office
failed to add entry: No such object at /usr/sbin/smbldap-populate line 499, <GEN1> line 223.
adding new entry: cn=Replicators,ou=groups,dc=example,dc=office,dc=example,dc=office
failed to add entry: No such object at /usr/sbin/smbldap-populate line 499, <GEN1> line 234.
entry sambaDomainName=EXOFFICE,dc=example,dc=office already exist. Updating it...

Please provide a password for the domain root: 
/usr/sbin/smbldap-passwd: user root doesn't exist
```

Here is some information:
-using Ubuntu 9.10 Server
-added ldap password to samba "smbpasswd -w pass"
-verified /etc/smbldap-tools/smbldap_bind.conf is correct
-pretty much followed the guides exactly, so everything else that should have been done, was.  

I'm not too familiar with LDAP, this is my first time implementing it... so I'm not sure how everything fits together.  I've googled my brains out on this error, but haven't found much information.  

Anyone have any ideas?

TIA.

---

