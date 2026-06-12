---
title: "LDAP authentication problem, please help explain this"
date: 2011-02-26
forum: Server Platforms
---

### Post by Caudovittatus on 2011-02-26
Hi,
 
I recently setup OpenLDAP on Ubuntu Server 10.04.2; I then messed up the configuration and decided to rebuild from a clean config.
 
I followed this guide initially (and was using it as reference for the reconfig):
 
[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)
 
The second time around I got as far as this:
 
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f backend.example.com.ldif
 
My only changes to the example from the tutorial (reproduced below) was that I replaced instances of dc=example,dc=com with ones appropriate for my config.
 
backend.example.com.ldif
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
```
 
The next command to run was this:
 
sudo ldapadd -x -D cn=admin,dc=example,dc=com -W -f frontend.example.com.ldif
 
Again using the example from the tutorial (reproduced below) but modified to replace dc=example,dc=com with my own values (my version didn't add users either):
 
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
userPassword: secret
 
dn: ou=people,dc=example,dc=com
objectClass: organizationalUnit
ou: people
 
dn: ou=groups,dc=example,dc=com
objectClass: organizationalUnit
ou: groups
 
dn: uid=john,ou=people,dc=example,dc=com
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
uid: john
sn: Doe
givenName: John
cn: John Doe
displayName: John Doe
uidNumber: 1000
gidNumber: 10000
userPassword: password
gecos: John Doe
loginShell: /bin/bash
homeDirectory: /home/john
shadowExpire: -1
shadowFlag: 0
shadowWarning: 7
shadowMin: 8
shadowMax: 999999
shadowLastChange: 10877
mail: john.doe@example.com
postalCode: 31000
l: Toulouse
o: Example
mobile: +33 (0)6 xx xx xx xx
homePhone: +33 (0)5 xx xx xx xx
title: System Administrator
postalAddress: 
initials: JD
 
dn: cn=example,ou=groups,dc=example,dc=com
objectClass: posixGroup
cn: example
gidNumber: 10000
```
 
This failed with the following message which did not happen first time round:
 
```
adding new entry "dc=example,dc=com"
ldap_add: Already exists (68)

```
 
In the first run, I had this output when running the above command:
```

adding new entry "dc=example,dc=com"
 
adding new entry "cn=admin,dc=example,dc=com"
 
adding new entry "ou=people,dc=example,dc=com"
 
adding new entry "ou=groups,dc=example,dc=com"
 
adding new entry "uid=john,ou=people,dc=example,dc=com"
 
adding new entry "cn=example,ou=groups,dc=example,dc=com"

```
 
I think the problem is something to do with nss_ldap and its configuration file (/etc/ldap.conf) which I'd installed in the first run through. I found that by:
a) Renaming /etc/ldap.conf to /etc/ldap.conf.bak
b) dpkg-reconfigure slapd
c) apt-get --purge remove slapd ldap-tools
d) apt-get install slapd ldap-tools
By doing the above in exactly that order, I could then run through and get frontend.example.com.ldif to populate as it had on the first run (note trying dpkg-reconfigure slapd and purging the slap.d directory and/or just renaming /etc/ldap.conf still yielded the error).
 
So I can work around the problem, but I don't understand the problem. Can anyone help with this? I'd like to know why, with nss_ldap installed and configured I can't populate the frontend.example.com.ldif file as described above.
 
I suspect that it may have something to do with the line in /etc/ldap.conf:
 
base dc=example,dc=com
 
However I'm not sure exactly how this interacts with the standard OpenLDAP tools like ldapadd and so I can't figure how to modify my commands accordingly.
 
Any advise would be appreciated as I would prefer to understand the issue than simply work around it.
 
Thanks

---

