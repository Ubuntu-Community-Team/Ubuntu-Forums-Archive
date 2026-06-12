---
title: "LDAP Replication on 8.10"
date: 2009-10-05
forum: Server Platforms
---

### Post by grylnsmn on 2009-10-05
I have been trying to enable replication between two servers (named murcielago and tortuga) using OpenLDAP 2.4.11-0ubuntu6.2 on 8.10.  I have followed the guide located [here]("https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html"), and I now have limited replication working.  It will replicate the configuration changes, but it won't replicate the backend data.

Below I have the settings from my cn=config setup for replication, as recommended by the guide (with my domain name changed to example.com, and my password changed to 12Password34).

```
richard@murcielago:~$ ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase={1}config
Enter LDAP Password: 
dn: olcDatabase={0}config,cn=config
objectClass: olcDatabaseConfig
olcDatabase: {0}config
olcRootDN: cn=admin,cn=config
olcRootPW: {crypt}PytMY/jCk78gI
olcSyncrepl: {0}rid=001 provider=ldap://murcielago.example.com binddn="cn=admin,cn
 =config" bindmethod=simple credentials=12Password34 searchbase="cn=config" type=r
 efreshAndPersist retry="5 5 300 5" timeout=1
olcSyncrepl: {1}rid=002 provider=ldap://tortuga.example.com binddn="cn=admin,cn=co
 nfig" bindmethod=simple credentials=12Password34 searchbase="cn=config" type=refr
 eshAndPersist retry="5 5 300 5" timeout=1
olcMirrorMode: TRUE

richard@murcielago:~$ ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase={1}hdb
Enter LDAP Password: 
dn: olcDatabase={1}hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcDbDirectory: /var/lib/ldap
olcSuffix: dc=example,dc=com
olcAccess: {0}to attrs=userPassword,shadowLastChange by dn="cn=admin,dc=example,dc
 =com" write by anonymous auth by self write by * none
olcAccess: {1}to dn.base="" by * read
olcAccess: {2}to * by dn="cn=admin,dc=example,dc=com" write by * read
olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcDbConfig: {0}set_cachesize 0 2097152 0
olcDbConfig: {1}set_lk_max_objects 1500
olcDbConfig: {2}set_lk_max_locks 1500
olcDbConfig: {3}set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcRootDN: cn=admin,dc=example,dc=com
olcSyncrepl: {0}rid=003 provider=ldap://murcielago.example.com binddn="cn=admin,dc
 =example,dc=com" bindmethod=simple credentials=12Password34 searchbase="dc=example,dc=com
 " type=refreshOnly interval=00:00:00:10 retry="5 5 300 5" timeout=1
olcSyncrepl: {1}rid=004 provider=ldap://tortuga.example.com binddn="cn=admin,dc=example
 ,dc=com" bindmethod=simple credentials=12Password34 searchbase="dc=example,dc=com" t
 ype=refreshOnly interval=00:00:00:10 retry="5 5 300 5" timeout=1
olcMirrorMode: TRUE


richard@tortuga:~$ ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase={1}config
Enter LDAP Password: 
dn: olcDatabase={0}config,cn=config
objectClass: olcDatabaseConfig
olcDatabase: {0}config
olcRootDN: cn=admin,cn=config
olcRootPW: {crypt}PytMY/jCk78gI
olcSyncrepl: {0}rid=001 provider=ldap://murcielago.example.com binddn="cn=admin,cn
 =config" bindmethod=simple credentials=12Password34 searchbase="cn=config" type=r
 efreshAndPersist retry="5 5 300 5" timeout=1
olcSyncrepl: {1}rid=002 provider=ldap://tortuga.example.com binddn="cn=admin,cn=co
 nfig" bindmethod=simple credentials=12Password34 searchbase="cn=config" type=refr
 eshAndPersist retry="5 5 300 5" timeout=1
olcMirrorMode: TRUE

richard@tortuga:~$ ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase={1}hdb
Enter LDAP Password: 
dn: olcDatabase={1}hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcDbDirectory: /var/lib/ldap
olcSuffix: dc=example,dc=com
olcAccess: {0}to attrs=userPassword,shadowLastChange by dn="cn=admin,dc=example,dc
 =com" write by anonymous auth by self write by * none
olcAccess: {1}to dn.base="" by * read
olcAccess: {2}to * by dn="cn=admin,dc=example,dc=com" write by * read
olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcDbConfig: {0}set_cachesize 0 2097152 0
olcDbConfig: {1}set_lk_max_objects 1500
olcDbConfig: {2}set_lk_max_locks 1500
olcDbConfig: {3}set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcRootDN: cn=admin,dc=example,dc=com
olcSyncrepl: {0}rid=003 provider=ldap://murcielago.example.com binddn="cn=admin,dc
 =example,dc=com" bindmethod=simple credentials=12Password34 searchbase="dc=example,dc=com
 " type=refreshOnly interval=00:00:00:10 retry="5 5 300 5" timeout=1
olcSyncrepl: {1}rid=004 provider=ldap://tortuga.example.com binddn="cn=admin,dc=example
 ,dc=com" bindmethod=simple credentials=12Password34 searchbase="dc=example,dc=com" t
 ype=refreshOnly interval=00:00:00:10 retry="5 5 300 5" timeout=1
olcMirrorMode: TRUE
```I am at my wit's end trying to figure this one out.  Any suggestions on what I might be missing?

---

