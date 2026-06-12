---
title: "Can't get through OpenLDAP Server docs"
date: 2010-06-30
forum: Server Platforms
---

### Post by panfist on 2010-06-30
I'm trying to follow the OpenLDAP docs that are part of the Ubuntu 10.04 Server Guide, listed [here]("https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html"):

I get about halfway through, to this command:

sudo ldapadd -x -D cn=admin,dc=example,dc=com -W -f frontend.example.com.ldif

When it asks me to "Enter LDAP Password:" and nothing I have tried works. I thought it might have been "olcRootPW: secret" set in the backend file in the step before, but that isn't working.

---

### Post by talz13 on 2010-07-08
I am at the same point while following [https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html) , but my olcRootPW from the backend file worked for me.  I am stuck with:```
jeff@server:~$ sudo ldapadd -x -D cn=admin,dc=server,dc=home -W -f frontend.server.home.ldif
[sudo] password for jeff:
Enter LDAP Password:
adding new entry "dc=server,dc=home"
ldap_add: Naming violation (64)
        additional info: value of single-valued naming attribute 'dc' conflicts with value present in entry


```

Here's my frontend.server.home.ldif file (with my password removed, of course):```
# Create top-level object in domain
dn: dc=server,dc=home
objectClass: top
objectClass: dcObject
objectclass: organization
o: Home Domain
dc: Home
description: LDAP for home network

# Admin user.
dn: cn=admin,dc=server,dc=home
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword: [secret]

dn: ou=people,dc=server,dc=home
objectClass: organizationalUnit
ou: people

dn: ou=groups,dc=server,dc=home
objectClass: organizationalUnit
ou: groups

dn: uid=john,ou=people,dc=server,dc=home
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

dn: cn=server,ou=groups,dc=server,dc=home
objectClass: posixGroup
cn: server
gidNumber: 10000


```

---

### Post by Devi1903 on 2010-07-08
Panfist:
The password on olcRootPW should work. Please post your LDIF for me to look at.

talz13:
Not entirely sure why you are receiving that error. One thing on your frontend.
> o: Home Domain
dc: Home
Should be server and not home. Make that change and see what happens.

---

### Post by lubumbax on 2010-08-11
I got stuck even earlier. 
After trying to configure the backend, I get an "implementation specific" error
at "olcDbIndex: objectClass eq". 

I have a feeling that it has something to do with libdb, but don't know what. This is a more detailed log of what I did:

First setups:
```
$ sudo apt-get --purge remove slapd ldap-utils
$ sudo rm -rf /var/lib/ldap /var/run/ldapi /var/run/slapd /etc/ldap
$ sudo apt-get install slapd ldap-utils
$ sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/cosine.ldif
$ sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/nis.ldif
$ sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/inetorgperson.ldif

  Output:
  SASL/EXTERNAL authentication started
  SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
  SASL SSF: 0
  adding new entry "cn=cosine,cn=schema,cn=config"
  (...the same for nis.ldif and inetorgperson.ldif...)

  Logs:
  ==> /var/log/syslog <==
  Aug 11 11:52:32 lennon slapd[14907]: connection_read(13): no connection!
  (...many times...)
```Configure the backend:
```
$ vi ~/tmp/backend.lan.ldif
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
        olcSuffix: dc=lan
        olcDbDirectory: /var/lib/ldap
        olcRootDN: cn=root,dc=lan
        olcRootPW: MYSECRET
        olcDbConfig: set_cachesize 0 2097152 0
        olcDbConfig: set_lk_max_objects 1500
        olcDbConfig: set_lk_max_locks 1500
        olcDbConfig: set_lk_max_lockers 1500
        olcDbIndex: objectClass eq
        olcLastMod: TRUE
        olcDbCheckpoint: 512 30
        olcAccess: to attrs=userPassword by dn="cn=root,dc=lan" write by anonymous auth by self write by * none
        olcAccess: to attrs=shadowLastChange by self write by * read
        olcAccess: to dn.base="" by * read
        olcAccess: to * by dn="cn=root,dc=lan" write by * read

$ sudo ldapadd -Y EXTERNAL -H ldapi:/// -f ~/tmp/backend.lan.ldif

  Output:
  SASL/EXTERNAL authentication started
  SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
  SASL SSF: 0
  adding new entry "cn=module,cn=config"

[B]  adding new entry "olcDatabase=hdb,cn=config"
  ldap_add: Other (e.g., implementation specific) error (80)
      additional info: <olcDbIndex> failed startup[/B]

  Logs:
  ==> /var/log/syslog <==
  Aug 11 12:10:42 lennon slapd[14907]: bdb(dc=lan): /var/lib/ldap: Permission denied
  Aug 11 12:10:42 lennon slapd[14907]: bdb(dc=lan): PANIC: Permission denied
  Aug 11 12:10:42 lennon slapd[14907]: bdb(dc=lan): unable to join the environment
  Aug 11 12:10:42 lennon slapd[14907]: bdb(dc=lan): /var/lib/ldap: Permission denied
  Aug 11 12:10:42 lennon slapd[14907]: hdb_db_open: database "dc=lan" cannot be opened, err -30974. Restore from backup!
  Aug 11 12:10:42 lennon slapd[14907]: bdb(dc=lan): txn_checkpoint interface requires an environment configured for the transaction subsystem
  Aug 11 12:10:42 lennon slapd[14907]: bdb_db_close: database "dc=lan": txn_checkpoint failed: Invalid argument (22).
  Aug 11 12:10:42 lennon slapd[14907]: backend_startup_one (type=hdb, suffix="dc=lan"): bi_db_open failed! (-30974)
  Aug 11 12:10:42 lennon slapd[14907]: olcDbIndex: value #0: <olcDbIndex> failed startup ()!
  Aug 11 12:10:42 lennon slapd[14907]: connection_read(13): no connection!
  Aug 11 12:10:42 lennon slapd[14907]: connection_read(13): no connection!
  Aug 11 12:10:42 lennon kernel: [ 7041.875741] type=1400 audit(1281521442.006:49):  operation="getattr" pid=14928 parent=1 profile="/usr/sbin/slapd" name="/var/lib/" pid=14928 comm="slapd" requested_mask="r" denied_mask="r" fsuid=128 ouid=0
  Aug 11 12:10:42 lennon kernel: [ 7041.876018] type=1400 audit(1281521442.006:50):  operation="getattr" pid=14928 parent=1 profile="/usr/sbin/slapd" name="/var/lib/" pid=14928 comm="slapd" requested_mask="r" denied_mask="r" fsuid=128 ouid=0
```The libraries currently loaded by slapd are:
```
$ sudo lsof -p `ps -e | grep slapd | cut -d' ' -f1` | awk '$9 ~ /lib\// { print $9 }' 2>/dev/null
  /usr/lib/sasl2/liblogin.so.2.0.23
  /usr/lib/sasl2/libcrammd5.so.2.0.23
  /usr/lib/sasl2/libplain.so.2.0.23
  /usr/lib/sasl2/libanonymous.so.2.0.23
**  /usr/lib/libdb-4.8.so**
  /usr/lib/sasl2/libsasldb.so.2.0.23
  /usr/lib/sasl2/libdigestmd5.so.2.0.23
  /lib/libcrypto.so.0.9.8
  /usr/lib/sasl2/libntlm.so.2.0.23
  /lib/libnss_nis-2.11.1.so
  /lib/libnss_compat-2.11.1.so
  /lib/libnss_files-2.11.1.so
  /lib/libgpg-error.so.0.4.0
  /lib/libgcrypt.so.11.5.2
  /lib/libz.so.1.2.3.3
  /usr/lib/libtasn1.so.3.1.7
  /lib/libkeyutils-1.2.so
  /usr/lib/libkrb5support.so.0.1
  /lib/libcom_err.so.2.1
  /usr/lib/libk5crypto.so.3.1
  /usr/lib/libkrb5.so.3.3
  /lib/libdl-2.11.1.so
  /lib/libnsl-2.11.1.so
  /lib/libc-2.11.1.so
  /lib/libpthread-2.11.1.so
  /lib/libwrap.so.0.7.6
  /usr/lib/libltdl.so.7.2.1
  /lib/libresolv-2.11.1.so
  /lib/libcrypt-2.11.1.so
  /usr/lib/libgnutls.so.26.14.12
  /usr/lib/libgssapi_krb5.so.2.2
  /usr/lib/libsasl2.so.2.0.23
  /usr/lib/libslp.so.1.0.1
  /usr/lib/libodbc.so.1.0.0
**  /usr/lib/libdb-4.7.so**
  /usr/lib/liblber-2.4.so.2.5.4
  /usr/lib/libldap_r-2.4.so.2.5.4
  /lib/ld-2.11.1.so

```And the installed packages:
```
$ dpkg --list *{db4,slapd,ldap}* | grep -e "^i"
  ii  db4.8-util                  4.8.24-1ubuntu1            Berkeley v4.8 Database Utilities
  ii  ldap-utils                  2.4.21-0ubuntu5.2          OpenLDAP utilities
  ii  libaprutil1-ldap            1.3.9+dfsg-3build1         The Apache Portable Runtime Utility Library 
  ii  libdb4.6                    4.6.21-16                  Berkeley v4.6 Database Libraries [runtime]
  ii  libdb4.7                    4.7.25-9                   Berkeley v4.7 Database Libraries [runtime]
  ii  libdb4.7-java               4.7.25-9                   Berkeley v4.7 Database Libraries for Java
  ii  libdb4.7-java-gcj           4.7.25-9                   Berkeley v4.7 Database Libraries for Java (n
  ii  libdb4.8                    4.8.24-1ubuntu1            Berkeley v4.8 Database Libraries [runtime]
  ii  libldap-2.4-2               2.4.21-0ubuntu5.2          OpenLDAP libraries
  ii  libmono-ldap1.0-cil         2.4.4~svn151842-1ubuntu4   Mono LDAP library (for CLI 1.0)
  ii  libmono-ldap2.0-cil         2.4.4~svn151842-1ubuntu4   Mono LDAP library (for CLI 2.0)
  ii  libmono-system-ldap1.0-cil  2.4.4~svn151842-1ubuntu4   Mono System.DirectoryServices library (for C
  ii  libmono-system-ldap2.0-cil  2.4.4~svn151842-1ubuntu4   Mono System.DirectoryServices library (for C
  ii  slapd                       2.4.21-0ubuntu5.2          OpenLDAP server (slapd)
```
Thanks in advance!

J. Carlos Muro
Imagination is more important than knowledge.. (A. Einstein)

---

