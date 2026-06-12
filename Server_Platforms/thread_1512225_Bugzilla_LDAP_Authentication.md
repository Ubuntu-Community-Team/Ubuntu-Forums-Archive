---
title: "Bugzilla LDAP Authentication"
date: 2010-06-17
forum: Server Platforms
---

### Post by Thyagaraj on 2010-06-17
I've Bugzilla installed successfully and i've a ldap server. In bugzilla under parameters i've ldap settings for bugzilla ldap authentication. could any one give me step by step guide to this configuration.....?

---

### Post by denarced on 2010-06-20
I have no particular knowledge about this subject but as a rule, people don't respond to questions like yours. It's not a clear concise question but an open ended "write me a tutorial" kind of question. I'm not being hostile, this is just my personal experience since I've had some hostility when I asked an open ended question :D

---

### Post by Thyagaraj on 2010-06-23
I want to configure bugzilla ldap authentication.I want to login with ldap account instead of bugzilla account.

I could not configure the ldap section on bugzilla page

Ldap server:ldap//ldap.server.com

Ldapbasedns: ?

Ldapbinddns: ?

---

### Post by Thyagaraj on 2010-10-26
I've bugzilla and ldap running on different ubuntu servers. I'm trying to confiugre bugzilla to authenticate with ldap credentials but not successful so far. I've attached the bugzilla ldap setup configuration file page:

Here is my output of **slapcat**:
```

dn: dc=mycompany,dc=net
objectClass: top
objectClass: dcObject
objectClass: organization
o: mycompany.net
dc: mycompany
structuralObjectClass: organization
entryUUID: 1ac8b74e-03f1-102e-896f-2b5fd871cc44
creatorsName:
createTimestamp: 20090713120447Z
entryCSN: 20090745120447.504592Z#000000#000#000000
modifiersName:
modifyTimestamp: 20090713120447Z

dn: cn=user1,dc=mycompany,dc=net
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
cn: user1
description: LDAP administrator
userPassword:: e2EKyeXB0fUJklnoEtzZDJoWDd4cXc=
structuralObjectClass: organizationalRole
entryUUID: 1ac8gbc4-03f1-102e-8970-2b5fd541cc44
creatorsName:
createTimestamp: 20090713120447Z
entryCSN: 20090713120904.903500Z#000000#000#000000
modifiersName: cn=user1,dc=mycompany,dc=net
modifyTimestamp: 20090713120904Z

dn: dc=Users,dc=mycompany,dc=net
objectClass: domain
dc: Users
structuralObjectClass: domain
entryUUID: c33f9ae8-03f1-102e-80b6-a7ba43564571
creatorsName: cn=user1,dc=mycompany,dc=net
createTimestamp: 20090713120935Z
entryCSN: 20090713120935.489424Z#000000#000#000000
modifiersName: cn=user1,dc=mycompany,dc=net
modifyTimestamp: 20090713120935Z

dn: uid=example,dc=Users,dc=mycompany,dc=net
structuralObjectClass: person
entryUUID: c672973a-03f1-102e-80b7-a7ba43494571
creatorsName: cn=user1,dc=mycompany,dc=net
createTimestamp: 20090713120935Z
gecos: Example user
uid: example
cn: Example user
homeDirectory: /home/ldaphome/
uidNumber: 9999
objectClass: posixAccount
objectClass: person
objectClass: shadowAccount
gidNumber: 9999
sn: Example user
shadowLastChange: 14438
userPassword:: IXtnhvDlwdH1CRVVEVWY4L3I5Tkky
loginShell: /bin/bash
entryCSN: 20100917100309.255985Z#000000#000#000000
modifiersName: cn=user1,dc=mycompany,dc=net
modifyTimestamp: 20100917100309Z

dn: dc=Groups,dc=mycompany,dc=net
objectClass: domain
dc: Groups
structuralObjectClass: domain
entryUUID: d0b193jk-03f1-102e-80b8-a7ba40094571
creatorsName: cn=user1,dc=mycompany,dc=net
createTimestamp: 20090713120952Z
entryCSN: 20090713120952.699029Z#000000#000#000000
modifiersName: cn=user1,dc=mycompany,dc=net
modifyTimestamp: 20090713120952Z

dn: uid=gopalath,dc=Users,dc=mycompany,dc=net
structuralObjectClass: inetOrgPerson
entryUUID: 288f4540-fb4d-102e-8de8-c32c54257882
creatorsName: cn=user1,dc=mycompany,dc=net
createTimestamp: 20100524065601Z
gecos: Thyagaraj
uid: gopalath
cn: Thyagaraj
homeDirectory: /home/gopalath
uidNumber: 1018
objectClass: posixAccount
objectClass: shadowAccount
objectClass: person
objectClass: inetOrgPerson
gidNumber: 100
sn: Thyagaraj
shadowLastChange: 14879
userPassword:: IXtjcnlwjkspFNFkwOHhxY0RV
loginShell: /bin/bash
entryCSN: 20100927113236.381965Z#000000#000#000000
modifiersName: cn=user1,dc=mycompany,dc=net
modifyTimestamp: 20100927113236Z

-------------------------------
-------------------------------
-------------------------------

```

---

### Post by Thyagaraj on 2010-10-27
somehow I fixed this issue!. Thanks to myself

---

### Post by danielmoros on 2012-01-28
I had error using LDAP login: 
 *user_verify_class*

I solved it doing this:

 aptitude install libnet-ldap-perl  libnet-ldapapi-perl    libnet-ldap-filterbuilder-perl libdbd-ldap-perl libauthen-simple-ldap-perl libapache-authznetldap-perl

---

