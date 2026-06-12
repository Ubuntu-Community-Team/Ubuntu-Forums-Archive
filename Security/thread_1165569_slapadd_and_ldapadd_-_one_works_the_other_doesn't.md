---
title: "slapadd and ldapadd - one works the other doesn't"
date: 2009-05-20
forum: Security
---

### Post by matthewboh on 2009-05-20
I'm trying to put up a openLDAP with Samba and I'm ready to tear my hair out!

I've followed several different guides trying to get it to work, but keep running into problems.

ldapsearch -x -W -D 'cn=admin,dc=imparisystems,dc=local' 'objectclass=*'

It prompts me for my password, and I get

```
# extended LDIF
#
# LDAPv3
# base <dc=imparisystems,dc=local> (default) with scope subtree
# filter: objectclass=*
# requesting: ALL
#

# imparisystems.local
dn: dc=imparisystems,dc=local
objectClass: top
objectClass: dcObject
objectClass: organization
o: Impari Systems, Inc.
dc: imparisystems

# admin, imparisystems.local
dn: cn=admin,dc=imparisystems,dc=local
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword:: e2NyeXB0fVNnZ1lIZjQzT1NkTG8=

# Users, imparisystems.local
dn: ou=Users,dc=imparisystems,dc=local
objectClass: organizationalUnit
ou: Users

# Groups, imparisystems.local
dn: ou=Groups,dc=imparisystems,dc=local
objectClass: organizationalUnit
ou: Groups

# Computers, imparisystems.local
dn: ou=Computers,dc=imparisystems,dc=local
objectClass: organizationalUnit
ou: Computers

# Idmap, imparisystems.local
dn: ou=Idmap,dc=imparisystems,dc=local
objectClass: organizationalUnit
ou: Idmap

# search result
search: 2
result: 0 Success

# numResponses: 7
# numEntries: 6

```

So I think that proves I have the right credentials.

My slapd.conf file has the following ACL entries
```
access to attrs=userPassword,shadowLastChange
        by dn="cn=admin,dc=imparisystems,dc=local" write
        by anonymous auth
        by self write
        by * none

access to dn.base="" by * read

access to *
        by dn="cn=admin,dc=imparisystems,dc=local" write
        by * read

```

And the root information is in slapd.conf as well
```
rootdn cn=admin,dc=imparisystems,dc=local
rootpw {SSHA}msKhbnUNzsaX0wG+p95IDlEy5dmva0LV
```

But if I try to do an ldapadd - I get

```
ldapadd -x -D cn=admin,dc=imparisystems,dc=local -f /tmp/ldif_output/cn\=config/cn\=schema/cn\=\{8\}misc.ldif -W
Enter LDAP Password: 
adding new entry "cn=misc,cn=schema,cn=config"
ldap_add: Insufficient access (50)
```
I've looked all over to try and find out what the problem is - where should I look - I can add entries using slapadd but not ldapadd. 

Thanks!

---

