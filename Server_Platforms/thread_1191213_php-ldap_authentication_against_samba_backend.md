---
title: "php-ldap authentication against samba backend"
date: 2009-06-18
forum: Server Platforms
---

### Post by kwadrofonik on 2009-06-18
Hello, I have fresh Server 9.04 with a working samba+LDAP PDC setup based on the stock Ubuntu OpenLDAP documentation. I'm trying to authenticate via the web using the above LDAP tree.
 
However the following command fails,
```
 
ldap_bind($ldap,"uid=itmgr,ou=people,dc=docunet,dc=mydomain,dc=ca","password")

```
 
```
Warning: ldap_bind() [[function.ldap-bind]("https://docunet.plaza.ca:442/function.ldap-bind")]: Unable to bind to server: Invalid credentials in /var/www/authenticate.php on line 31
permission denied 
```
 
The same account works find when I connect with both a windows and linux samba client. What am I missing?
 
Here are my indexes (domain changed to mydomain but is a valid FQDN):
```
dn: olcDatabase={1}hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcDbDirectory: /var/lib/ldap
olcSuffix: dc=docunet,dc=mydomain,dc=ca
olcAccess: {0}to attrs=userPassword,shadowLastChange by dn="cn=admin,dc=docune
 t,dc=mydomain,dc=ca" write by anonymous auth by self write by * none
olcAccess: {1}to dn.base="" by * read
olcAccess: {2}to * by dn="cn=admin,dc=docunet,dc=mydomain,dc=ca" write by * read
olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcDbConfig: {0}set_cachesize 0 2097152 0
olcDbConfig: {1}set_lk_max_objects 1500
olcDbConfig: {2}set_lk_max_locks 1500
olcDbConfig: {3}set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcDbIndex: entryUUID eq
olcDbIndex: uid eq,pres,sub
olcDbIndex: uidNumber eq
olcDbIndex: gidNumber eq
olcDbIndex: loginShell eq
olcDbIndex: memberUid eq,pres,sub
olcDbIndex: uniqueMember eq,pres
olcDbIndex: sambaSID eq
olcDbIndex: sambaPrimaryGroupSID eq
olcDbIndex: sambaGroupType eq
olcDbIndex: sambaSIDList eq
olcDbIndex: sambaDomainName eq
olcDbIndex: default sub
```
 
my tree is completely stock
```
cn=admin
 ou=Computers
 ou=groups (10)
 ou=Idmap
 ou=people (4)
    uid=itmgr
    uid=john
    uid=nobody
    uid=root
 sambaDomainName=docunet.mydomain.ca

```
 
Thanks a million!

---

### Post by kwadrofonik on 2009-06-19
I figured it out. I was adding users with ldapscripts instead of smbldap-useradd -a 
 
The latter creates both the samba attributes and the posix attributes and synchonizes the two password fields.

---

