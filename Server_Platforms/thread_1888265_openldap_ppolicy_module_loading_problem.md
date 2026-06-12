---
title: "openldap ppolicy module loading problem"
date: 2011-11-28
forum: Server Platforms
---

### Post by dhchen on 2011-11-28
Hello,
 
I'm trying to enforce password policy on my ldap auth mechnism. But I always fails to load ppolicy module as slapd's supportedControl does not show its OID 1.3.6.1.4.1.42.2.27.8.5.1. Is there any suggestions? I'm using 10.04.3 with the following module configuration:
 
dn: cn=module{0},cn=config
objectClass: olcModuleList
cn: module{0}
olcModulePath: /usr/lib/ldap
olcModuleLoad: {0}back_hdb.so
olcModuleLoad: {1}ppolicy.so

---

