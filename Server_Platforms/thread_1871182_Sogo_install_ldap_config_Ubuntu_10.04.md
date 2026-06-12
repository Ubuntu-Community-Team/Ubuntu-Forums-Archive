---
title: "Sogo install ldap config Ubuntu 10.04"
date: 2011-10-28
forum: Server Platforms
---

### Post by shaunkimura on 2011-10-28
Looking for some direction I have been trying to install SoGo on 10.04 and keep getting stuck on the backend and front end ldap config. After creating the backend.example.com.ldif with the below:
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
olcSuffix: dc=primaryfreight,dc=info
olcDbDirectory: /var/lib/ldap
olcRootDN: cn=admin,dc=mydomain,dc=info
olcRootPW: mypassword
olcDbConfig: set_cachesize 0 2097152 0
olcDbConfig: set_lk_max_objects 1500
olcDbConfig: set_lk_max_locks 1500
olcDbConfig: set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcAccess: to attrs=userPassword by dn="cn=admin,dc=mydomain,dc=info" write by anonymous auth by self write by * none
olcAccess: to attrs=shadowLastChange by self write by * read
olcAccess: to dn.base="" by * read
olcAccess: to * by dn="cn=admin,dc=mydomain,dc=info" write by * read
```I then run:
```
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f backend.example.com.ldif
```I get hit with:
```
ldap_add: Other (e.g., implementation specific) error (80)
        additional info: <olcModuleLoad> handler exited with 1
```and not sure were to go from here...

---

### Post by shaunkimura on 2011-10-28
Ok well found out the above error occurs when it has already been run... Ok next step create the frontend.example.info.ldif

```
# Create top-level object in domain
dn: dc=mydomain,dc=info
objectClass: top
objectClass: dcObject
objectclass: organization
o: mydomain Organization
dc: mydomain
description: mydomain LDAP Server

# Admin user.
dn: cn=admin,dc=mydomain,dc=info
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword: mypassword
```

then run:
```
**sudo ldapadd -x -D cn=admin,dc=example,dc=com -W -f frontend.example.info.ldif**
``` and now I get:
Enter LDAP Password: 
ldap_bind: Invalid credentials (49)

So my question is were do I edit this LDAP password cause I have tried everywhere but I must be missing something... Help...

---

