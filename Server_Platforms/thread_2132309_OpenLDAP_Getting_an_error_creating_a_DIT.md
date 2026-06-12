---
title: "OpenLDAP: Getting an error creating a DIT"
date: 2013-04-04
forum: Server Platforms
---

### Post by Stilgar on 2013-04-04
I'm still using Ubuntu 10.04.4 LTS Server (can't take it down to do a dist upgrade right now).

I'm trying to get slapd working, and I'm following [this guide]("https://help.ubuntu.com/community/OpenLDAPServer").

I get to the "Creating a DIT with the RTC System" part of it.

I'm using the command 

```
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f example.ldif
```

To create the following database:

```
dn: olcDatabase=hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: hdb
olcDbDirectory: /var/lib/ldap
olcSuffix: dc=atlanticwindows,dc=com
olcAccess: {0}to attrs=userPassword,shadowLastChange by self write by anonymous auth by dn="cn=admin,dc=atlanticwindows,dc=com" write by * no$
olcAccess: {1}to dn.base="" by * read
olcAccess: {2}to * by self write by dn="cn=admin,dc=atlanticwindows,dc=com" write by * read
olcLastMod: TRUE
olcRootDN: cn=admin,dc=atlanticwindows,dc=com
olcRootPW: {SSHA}+e19ofjm5LHeU5ahmZeewSnDNwDucFzq
olcDbCheckpoint: 512 30
olcDbConfig: {0}set_cachesize 0 2097152 0
olcDbConfig: {1}set_lk_max_objects 1500
olcDbConfig: {2}set_lk_max_locks 1500
olcDbConfig: {3}set_lk_max_lockers 1500
olcDbIndex: objectClass eq

```

But it doesn't work. I get the following error:

```
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "olcDatabase=hdb,cn=config"
ldap_add: Invalid syntax (21)
        additional info: objectClass: value #1 invalid per syntax

```

Does anyone know what the problem could be? Do I need to install something? It seems like something is missing.

Thanks.

---

