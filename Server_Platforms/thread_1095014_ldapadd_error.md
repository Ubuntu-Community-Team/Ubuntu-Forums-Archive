---
title: "ldapadd error"
date: 2009-03-13
forum: Server Platforms
---

### Post by roary on 2009-03-13
Hi

I've a problem on Ubuntu 8.10 server when trying to setup ldap for samba.  The error is when I try to do the following: -

[INDENT]sudo ldapadd -x -D cn=admin,cn=config -W -f /tmp/ldif_output/cn\=config/cn\=schema/cn\=\{12\}samba.ldif[/INDENT]
I get the following error:-

[INDENT]adding new entry "cn=samba,cn=schema,cn=config"
ldap_add: Naming Violation (64)
[INDENT]additional info: value of naming attribute 'cn' is not present in entry[/INDENT][/INDENT]

I'm a novice and would appreciate any help.

Cheers
Karl

---

### Post by hm74us on 2010-02-02
ldap_add: Naming violation (64)
        additional info: value of naming attribute 'dc' is not present in entry


This message has to do with the order of the attributes of the Root node, the following order should be used.  Replace example and Company with your own information.
 # Root node
dn: dc=example,dc=com
objectclass: dcObject
objectclass: organization
o: Company
dc: example

~H3c70r

---

