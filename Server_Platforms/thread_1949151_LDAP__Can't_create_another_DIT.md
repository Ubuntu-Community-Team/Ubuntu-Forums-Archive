---
title: "LDAP : Can't create another DIT"
date: 2012-03-29
forum: Server Platforms
---

### Post by carlossg00 on 2012-03-29
Hello All,

After spending hours and hours reading various Ubuntu guides, and other related resources, I couldn' find a solution, so I claim for your help!!!

Ubuntu Version: Oneric Ocelot 11.10


My question is simple, just to to create another DIT, these are the steps I follow

* Created a new dir under /var/lib/ldap (755 to openldap user)
* added new ldif with database information 

```

sudo ldapadd -Y EXTERNAL -H ldapi://// -f scratchdit.ldif

``````


dn: olcDatabase=hdb
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: hdb
olcDbDirectory: /var/lib/ldap/example.com
olcSuffix: dc=example,dc=com
olcAccess: {0}to attrs=userPassword,shadowLastChange by self write by anonymou
 s auth by dn="cn=admin,dc=example,dc=com" write by * none
olcAccess: {1}to dn.base="" by * read
olcAccess: {2}to * by self write by dn="cn=admin,dc=example,dc=com" write by * read
olcLastMod: TRUE
olcRootDN: cn=admin,dc=example,dc=com
olcRootPW:: e1NTSEF9NlZSbnN2bkJEWVdSbFFoS1ZWOE1TckxTdWhsc0NvSVg=
olcDbCheckpoint: 512 30
olcDbConfig: {0}set_cachesize 0 2097152 0
olcDbConfig: {1}set_lk_max_objects 1500
olcDbConfig: {2}set_lk_max_locks 1500
olcDbConfig: {3}set_lk_max_lockers 1500
olcDbIndex: objectClass eq

```* test that its included in RTC (cn=config)

```

dn: cn=config
dn: cn=module{0},cn=config
...
dn: olcDatabase={-1}frontend,cn=config
dn: olcDatabase={0}config,cn=config
dn: olcDatabase={1}hdb,cn=config
olcSuffix: dc=nodomain
dn: olcDatabase={2}hdb,cn=config
olcSuffix: dc=example,dc=com

```* perform search on dc=domain

```

ldapsearch -xLLL -b "dc=nodomain" dn

``````
dn: dc=nodomain

dn: cn=admin,dc=nodomain
```* perform search on dc=example,dc=com
```

sudo ldapsearch -Q -LLL -Y EXTERNAL -H ldapi:/// -b 'dc=example,dc=com' dn 

```No Such object (32)

or
```

ldapsearch -xLLL -b "dc=nodomain" dn

```No Such object(32)


I've also modified /etc/ldap/slapd.d/cn=config/olcDatabase={1}hdb.ldif and replaced "dc=nodomain" to "dc=example,dc=com" or similar and restart slapd. but no success.

I am completely stuck, Installing slapd package scripts might be helpfull but don't know where to find them.  

Any help?

Thans in advanced.

---

### Post by carlossg00 on 2012-03-31
Problem was simple,

New database need to be populated to performs any search.

```
# Create top-level object in domain
dn: dc=example,dc=com
objectClass: top
objectClass: dcObject
objectclass: organization
o: Example Organization
dc: Example
description: LDAP Example 

# Admin user.
dn: cn=admin,dc=example,dc=com
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword: 1234
```

```
ldapadd -x -D cn=admin,dc=example,dc=com -W -f frontend.example.com.ldif
```

---

