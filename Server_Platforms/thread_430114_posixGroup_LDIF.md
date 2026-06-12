---
title: "posixGroup LDIF"
date: 2007-05-01
forum: Server Platforms
---

### Post by taenus on 2007-05-01
I'm working on populating an OpenLDAP server (Dapper) for pam authentication.  I'm basing it off a previous OpenSuSE 10.2 (please, no snickering).  I'm having trouble import LDIFs for my groups.  The following is and example:

(this imports on OpenSuSE)

# org.X.admins
dn: cn=admins,dc=X,dc=org
changetype: add
objectClass: groupOfNames
objectClass: top
objectClass: posixGroup
cn: admins
gidNumber: 1001
member: cn=admin,dc=X,dc=org

I get the following error:

adding new entry "cn=admins,dc=X,dc=org"
ldap_add: Object class violation (65)
        additional info: invalid structural object class chain (groupOfNames/posixGroup)

Now, if I strip it down a little, this will import:

dn: cn=admins,dc=X,dc=org
changetype: add
objectClass: posixGroup
cn: admins
gidNumber: 1001

I don't see though how this is supposed to tie to a user without the member entries.

I'm pretty sure this is schema issue.  I've noteded differances.in the scemas, as the OpenSuSE is actually a newer version of OpenLDAP.  Dapper is running 2.2.26, while OpenSuSE is 2.3.27.

---

