---
title: "OpenLDAP help - Naming violation (64)"
date: 2010-11-09
forum: Server Platforms
---

### Post by yeleek on 2010-11-09
Am trying to follow instructions here to create OpenLDAP server at home

[http://doc.ubuntu.com/ubuntu/serverguide/C/openldap-server.html](http://doc.ubuntu.com/ubuntu/serverguide/C/openldap-server.html)

Both slapd ldap-utils are installed, and i've followed the article, 
completing the first steps and then running
```
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f backend.keeley.local.ldif
```

which seems to work

SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=module,cn=config"

adding new entry "olcDatabase=hdb,cn=config"

and in my case is called 'backend.keeley.local.ldif' and contains

```
# Load dynamic backend modules
dn: cn=module,cn=config
objectClass: olcModuleList
cn: module
olcModulepath: /usr/lib/ldap
olcModuleload: back_hdb

# Database settings
dn: olcDatabase=hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcSuffix: dc=keeley,dc=local
olcDbDirectory: /var/lib/ldap
olcRootDN: cn=admin,dc=keeley,dc=local
olcRootPW: Scr0at123
olcDbConfig: set_cachesize 0 2097152 0
olcDbConfig: set_lk_max_objects 1500
olcDbConfig: set_lk_max_locks 1500
olcDbConfig: set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcAccess: to attrs=userPassword by dn="cn=admin,dc=keeley,dc=local" write by anonymous auth by self write by * none
olcAccess: to attrs=shadowLastChange by self write by * read
olcAccess: to dn.base="" by * read
olcAccess: to * by dn="cn=admin,dc=keeley,dc=local" write by * read
```

then created 'frontend.keeley.local.ldif' which contains

```
# Create top-level object in domain
dn: dc=keeley,dc=local
objectClass: top
objectClass: dcObject
objectclass: organization
o: Example Organization
dc: Example
description: LDAP Example 

# Admin user.
dn: cn=admin,dc=keeley,dc=local
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword: Scr0at123

dn: ou=people,dc=keeley,dc=local
objectClass: organizationalUnit
ou: people

dn: ou=groups,dc=keeley,dc=local
objectClass: organizationalUnit
ou: groups

dn: uid=ben,ou=people,dc=keeley,dc=local
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
uid: bk
sn: k
givenName: Ben
cn: Ben
displayName: Ben
uidNumber: 1000
gidNumber: 10000
userPassword: password
gecos: Ben K
loginShell: /bin/bash
homeDirectory: /home/bk
shadowExpire: -1
shadowFlag: 0
shadowWarning: 7
shadowMin: 8
shadowMax: 999999
shadowLastChange: 10877
mail: removed
postalCode: 
l: 
o: 
mobile:
homePhone:
title: System Administrator
postalAddress: 
initials: BK

dn: cn=example,ou=groups,dc=keeley,dc=local
objectClass: posixGroup
cn: example
gidNumber: 10000
```

if I then run

 ```
sudo ldapadd -x -D cn=admin,dc=keeley,dc=local -W -f frontend.keeley.local.ldif 
```

am getting the following message

sudo ldapadd -x -D cn=admin,dc=keeley,dc=local -W -f frontend.keeley.local.ldif 
Enter LDAP Password: 
adding new entry "dc=keeley,dc=local"
ldap_add: Naming violation (64)
	additional info: value of single-valued naming attribute 'dc' conflicts with value present in entry

Any ideas please?

Thank you

---

### Post by yeleek on 2010-11-10
Anyone?

---

### Post by sprocket888 on 2010-11-10
I just ran into this problem after following the Ubuntu tutorial on how to set up the LDAP.

I believe that your problem is on the 7th line of your frontend ldif file

Change

dc: Example

To

dc: keeley

This dc entry needs to match your domain name.

---

### Post by yeleek on 2010-11-10
Thank you so much - ashamed I missed that :oops:

---

### Post by lytithwyn on 2011-02-01
I had the same problem.  I'm just learning ldap, and I'd done a global search and replace on dc=example,dc=com, but I didn't see that other reference.

---

### Post by glide on 2012-01-19
Thank you I did exactly the same error :)

---

### Post by gcoram on 2012-11-18
me too, might be worth adding a "Be sure to replace dc:..." in the doc.
Thanks for the answer sprocket

---

