---
title: "[SOLVED] Can't add objects to my LDAP server. (phpldapadmin, smbldap-tools)"
date: 2007-08-24
forum: Server Platforms
---

### Post by h.aling on 2007-08-24
I'm unable to add any user to my freshly installed LDAP server (gutsy). No matter what I do, I keep getting the following errors:

Manually adding UID through phpLDAPadmin - 1.0.2
```
Could not add the object to the LDAP server.
 
LDAP said: Object class violation
Error number: 0x41 (LDAP_OBJECT_CLASS_VIOLATION)
Description: You tried to perform an operation that would cause an undefined attribute to exist or that would remove a required attribute, given the current list of ObjectClasses. This can also occur if you do not specify a structural objectClass when creating an entry, or if you specify more than one structural objectClass.
```

smbldap-populate (smbldap-tools)
```
$ sudo smbldap-populate 
Populating LDAP directory for domain MSHOME (S-1-5-21-406113952-1193301398-3047728428)
(using builtin directory structure)

Use of uninitialized value in concatenation (.) or string at /usr/sbin/smbldap-populate line 171.
entry dc=example,dc=intra already exist. 
entry dc=example,dc=intra already exist. 
entry ou=groups,dc=example,dc=intra already exist. 
entry ou=computers,dc=example,dc=intra already exist. 
entry ou=idmap,dc=example,dc=intra already exist. 
adding new entry: uid=root,dc=example,dc=intra
failed to add entry: objectclass: value #4 invalid per syntax at /usr/sbin/smbldap-populate line 495, <GEN1> line 7.
adding new entry: uid=nobody,dc=example,dc=intra
failed to add entry: objectclass: value #4 invalid per syntax at /usr/sbin/smbldap-populate line 495, <GEN1> line 8.
adding new entry: cn=Domain Admins,ou=groups,dc=example,dc=intra
failed to add entry: objectclass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 495, <GEN1> line 9.
adding new entry: cn=Domain Users,ou=groups,dc=example,dc=intra
failed to add entry: objectclass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 495, <GEN1> line 10.
adding new entry: cn=Domain Guests,ou=groups,dc=example,dc=intra
failed to add entry: objectclass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 495, <GEN1> line 11.
adding new entry: cn=Domain Computers,ou=groups,dc=example,dc=intra
failed to add entry: objectclass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 495, <GEN1> line 12.
adding new entry: cn=Administrators,ou=groups,dc=example,dc=intra
failed to add entry: objectclass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 495, <GEN1> line 16.
adding new entry: cn=Account Operators,ou=groups,dc=example,dc=intra
failed to add entry: objectclass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 495, <GEN1> line 18.
adding new entry: cn=Print Operators,ou=groups,dc=example,dc=intra
failed to add entry: objectclass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 495, <GEN1> line 19.
adding new entry: cn=Backup Operators,ou=groups,dc=example,dc=intra
failed to add entry: objectclass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 495, <GEN1> line 20.
adding new entry: cn=Replicators,ou=groups,dc=example,dc=intra
failed to add entry: objectclass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 495, <GEN1> line 21.
adding new entry: sambaDomainName=example.intra,dc=example,dc=intra
failed to add entry: invalid DN at /usr/sbin/smbldap-populate line 495, <GEN1> line 21.

Please provide a password for the domain root: 
/usr/sbin/smbldap-passwd: user root doesn't exist
```
(I've substituted my domain with 'example')

```
$ sudo smbldap-useradd -a -m test
Error looking for next uid at /usr/share/perl5/smbldap_tools.pm line 1044.
```

Help?


-H-

---

### Post by h.aling on 2007-08-24
FOUND IT!!!

[LIST=1]
[*]Install samba-doc
[*]zcat /usr/share/doc/samba-doc/examples/LDAP/samba.schema.gz to /etc/ldap/schema/samba.schema
[*]add the schema to /etc/ldap/slapd.conf
[/LIST]

But why isn't this schema installed with samba or smbldap-tools:confused:

-H-

---

