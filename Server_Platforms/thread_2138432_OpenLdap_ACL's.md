---
title: "OpenLdap ACL's"
date: 2013-04-24
forum: Server Platforms
---

### Post by Waynerd on 2013-04-24
Hi,

I am running OpenLdap 2.4.28 on Ubuntu 12.04
Everything is working fine expect that i cant add modify the ACL's

I want to allow LdapAdmins to do changes in the DIT and Account Manager should be allowed to do changes on Users.

When I try to edit the ACL with changetype: modify replace or delete/add
I get this error:

ldap_modify: Other (e.g., implementation specific) error (80)
    additional info: <olcAccess> handler exited with 1

When I just try to add the entry it shows like this:

olcAccess:: ezN9dG8gKiBieSBkbi5iYXNlPSJjbj10b2J5LG91PXVzZXJzLGRjPWtpdGVzeXN0ZW
 1zLGRjPWNvbSIgd3JpdGUgIA==

-----------
The Standart ACL:

dn: olcDatabase={1}hdb,cn=config
olcAccess: {0}to attrs=userPassword,shadowLastChange by self write by anonymou
 s auth by dn="cn=admin,dc=company,dc=com" write by * none
olcAccess: {1}to dn.base="" by * read
olcAccess: {2}to * by self write by dn="cn=admin,dc=company,dc=com" write 
 by * read



what I tryed so far:

dn: olcDatabase={1}hdb,cn=config
changetype: modify
delete: olcAccess
olcAccess: {2}
-
dn: olcDatabase={1}hdb,cn=config
add: olcAccess
olcAccess: to * 
 by self write
 by dn="cn=someuser,ou=users,dc=company,dc=com" manage  #tryed also with dn.base/dn.exact and also write instead of manage, also with groupOfNames and group.exact
 by dn="cn=admin,dc=company,dc=com" write 
 by * read 

#######################

dn: olcDatabase={1}hdb,cn=config
add: olcAccess
olcAccess: to * 
 by dn.base="cn=someuser,ou=users,dc=company,dc=com" write 

thanks for you help,
Peter

---

