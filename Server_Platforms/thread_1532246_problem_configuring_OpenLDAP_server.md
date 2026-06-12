---
title: "problem configuring OpenLDAP server"
date: 2010-07-16
forum: Server Platforms
---

### Post by tommi88 on 2010-07-16
hi guys...i have a problem in configuring OpenLDAP server...im stuck at the part where i have to add the 'backend.example.com.ldif'...everytime i perform this action 'sudo ldapadd -Y EXTERNAL -h ldapi:/// -f backend.example.com.ldif',i will get this two errors...

- ldapadd: invalid format(line 1) entry = ""
- ldapadd: invalid format(line 42) entry olcDatbase=hdb,cn=config

my backend.example.com.ldif is like this : 

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
olcSuffix: dc=example,dc=com
olcDbDirectory: /var/lib/ldap
olcRootDN: cn=admin,dc=example,dc=com
olcRootPW: secret
olcDbConfig: set_cachesize 0 2097152 0
olcDbConfig: set_lk_max_objects 1500
olcDbConfig: set_lk_max_locks 1500
olcDbConfig: set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcAccess: to attrs=userPassword by dn="cn=admin,dc=example,dc=com" write by anonymous auth by self write by * none
olcAccess: to attrs=shadowLastChange by self write by * read
olcAccess: to dn.base="" by * read
olcAccess: to * by dn="cn=admin,dc=example,dc=com" write by * read

has anyone faced this problem before?

---

