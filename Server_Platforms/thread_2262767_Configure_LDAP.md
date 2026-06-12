---
title: "Configure LDAP"
date: 2015-01-27
forum: Server Platforms
---

### Post by NewComer15 on 2015-01-27
Hello guys,
i am trying to make a directoryowner.
I made the file base.ldif with the following text.

dn:dc=meinedomain,dc=de #This should be the directoryowner account
objectClass: dcObject
objectClass: organization
o: meinedomain
dc: meinedomain

dn:cn=admin,dc=schulcloud,dc=de #This is the admin account
objectClass: organizationalRole
cn: adminThen i tipped ldapadd -x -h localhost -W -D cn=admin,dc=schulcloud,dc=de -f base.ldif

and following error arrupts 

adding new entry "dc=meinedomain,dc=local" 
ldap_add: Server is unwilling to perform (53)
	additional info: no global superior knowledge
Can someone help me?

Sorry for my bad English

Greets 
NewComer

---

