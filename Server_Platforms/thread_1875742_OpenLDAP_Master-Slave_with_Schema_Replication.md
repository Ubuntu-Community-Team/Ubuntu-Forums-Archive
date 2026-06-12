---
title: "OpenLDAP: Master-Slave with Schema Replication"
date: 2011-11-05
forum: Server Platforms
---

### Post by MyKey0815 on 2011-11-05
I using a Ubuntu 10.04 Domain with several member servers. Now i want to create a backup of my LDAP-Database.
 
I didn´t find a HowTo for replicating of data and SCHEMA from Master to one (or more) slaves.
 
My Servers are all with Ubuntu 10.04 TLS Server (only Console) 
OpenLDAP 2.4.21-0ubuntu5.5
 
What is the easiest and fastest way to synchronize ALL data from openldap to other servers?
 
Thanks
Michael

---

### Post by MyKey0815 on 2011-11-10
I´m a little step closer to my goal ;-)
 
In a book about Openldap i have read the way to replicate the cn=config-data. But the author descripte the slapd.conf method. My OpenLDAP use the database-backend. so I try to combine it and most of them works fine
 
On the Master I have import following LDIF
```
dn: cn=config
changetype: modify
add: olcReferral
olcReferral: "ldap://ldap.example.de"
 
dn: cn=module{0},cn=config
changetype: modify
add: olcModuleLoad
olcModuleLoad: syncprov
 
dn: olcOverlay=syncprov,olcDatabase={0}config,cn=config
changetype: add
objectClass: olcOverlayConfig
objectClass: olcSyncProvConfig
olcOverlay: syncprov
 
dn: olcOverlay=syncprov,olcDatabase={1}hdb,cn=config
changetype: add
objectClass: olcOverlayConfig
objectClass: olcSyncProvConfig
olcOverlay: syncprov
 
dn: olcDatabase={0}config,cn=config
changetype: modify
add: olcSyncrepl
olcSyncrepl: rid=002 provider=ldap://ldap.example.de type=refreshAndPersist retry="5 +" searchbase="cn=config" filter="(!(olcDatabase={0}config))" bindmethod=simple binddn="cn=admin,dc=example,dc=de" credentials=secret
add: olcUpdateRef
olcUpdateRef: ldap://ldap.example.de
 
dn: olcDatabase={1}hdb,cn=config
changetype: modify
add: olcSyncRepl
olcSyncRepl: rid=001 provider=ldap://ldap.example.de type=refreshAndPersist retry="5 +" searchbase="dc=example,dc=de" bindmethod=simple binddn="cn=admin,dc=example,dc=de" credentials=secret
add: olcUpdateRef
olcUpdateRef: [ldap://ldap.example.de](ldap://ldap.example.de)
```
 
On the Client-LDAP I import the following LDIF
 
```
dn: cn=config
#objectClass: olcGlobal
#cn: config
changetype: modify
add: olcReferral
olcreferral: ldap://ldap.example.de
 
dn: olcDatabase={0}config,cn=config
objectClass: olcDatabaseConfig
olcDatabase: {0}config
olcSyncRepl: rid=002 provider="ldap://ldap.example.de" binddn="cn=admin,dc=example,dc=de" bindmethod=simple credentials=secret searchbase="cn=config" filter="(!olcDatabase={0}config)" type=refreshAndPersist retry="10 +"
olcRootDN: cn=admin,dc=example,dc=de
olcUpdateRef: [ldap://ldap.example.de](ldap://ldap.example.de)
```
 
As result the complate ldap will be replicated. But when i restart the Slave-LDAP-Server then come up following error:
 
```
Starting OpenLDAP: slapd - failed.
The operation failed but no output was produced. For hints on what went
wrong please refer to the system's logfiles (e.g. /var/log/syslog) or
try running the daemon in Debug mode like via "slapd -d 16383" (warning:
this will create copious output).
 
Below, you can find the command line options used by this script to
run slapd. Do not forget to specify those options if you
want to look to debugging output:
  slapd -h 'ldap:/// ldapi:///' -g openldap -u openldap -F /etc/ldap/slapd.d/
```
 
And in syslog i find following entry:
```
Nov  9 20:54:03 SMS002092 slapd[3376]: @(#) $OpenLDAP: slapd 2.4.21 (Jun  2 2011 19:36:19) $#012#011buildd@allspice:/build/buildd/openldap-2.4$
Nov  9 20:54:03 SMS002092 slapd[3376]: config error processing olcDatabase={2}config,cn=config:
Nov  9 20:54:03 SMS002092 slapd[3376]: slapd stopped.
Nov  9 20:54:03 SMS002092 slapd[3376]: connections_destroy: nothing to destroy.
```
 
I can understand the error: ALL data will replicated and on the Slave another config [olcDatatbase={2}config) will be created. How can I avoid the creation of the second, incomplete database?

---

