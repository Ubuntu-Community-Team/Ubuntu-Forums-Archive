---
title: "Adding external LDIF file to LDAP directory"
date: 2013-12-06
forum: Ubuntu, Linux and OS Chat
---

### Post by alapan.mukherjee35 on 2013-12-06
Hi,

I am configuring a LDAP server on Linux. I am trying to move my LDIF (entries.ldif) to the LDAP directory with the command :

sudo ldapadd -Y EXTERNAL -H ldapi:/// -f entries.ldif

but I am getting the error 
ldap_add: Server is unwilling to perform (53)
additional info: no global superior knowledge

My slapd.conf file is ;
include   /etc/ldap/schema/core.schema
include   /etc/ldap/schema/cosine.schema
include   /etc/ldap/schema/nis.schema
pidfile   /var/run/slapd/slapd.pid
argsfile  /var/run/slapd/slapd.args
loglevel  sync stats

access to attrs=userPassword
        by self write
        by dn="cn=manager,dc=dcslabs,dc=fi" write
        by * auth

access to * by * read

# Set cn=manager to be your rootdn (you have to extend this!),
# and assign password for it by using slappasswd command.
# Use MD5 hashing for password manager.
moduleload back_bdb.la
backend bdb
database bdb
suffix "dc=dcslabs,dc=fi"
directory /var/lib/ldap
rootdn "cn=manager,dc=dcslabs,dc=fi"
rootpw y9t+Kx7VZs63lq8t8HIFow==
password-hash {MD5}

index objectClass eq
index cn,uid, eq,pres,sub


ENTRIES.LDIF

# This is the start of the tree.
dn: dc=dcslabs,o=fi
objectClass: dcObject
objectClass: Organization
objectClass: top
dc: dcslabs
o: dcslabs

dn: cn=manager,dc=dcslabs,dc=fi
objectClass: simpleSecurityObject
objectClass: organizationalRole
objectClass: top
cn: manager
userPassword: bond007

dn: ou=users,dc=dcslabs,dc=fi
objectClass: organizationalUnit
ou: users


dn: uid=lab2,ou=users,dc=dcslabs,dc=fi
uid: lab2
cn: lab2
objectClass: account
objectClass: posixAccount
objectClass: shadowAccount
objectClass: top
userPassword: bond007
homeDirectory: /home/labrat
gecos: lab2
shadowLastChange: 15300
shadowExpire: 16000
shadowMin: 0
shadowWarning: 0
shadowMax: 1000

dn: uid=lab3,ou=users,dc=dcslabs,dc=fi
uid: lab3
cn: lab3
objectClass: account
objectClass: posixAccount
objectClass: shadowAccount
objectClass: top
userPassword: bond007
loginShell: /bin/bash
uidNumber: 2001
gidNumber: 1000
homeDirectory: /home/labrat
gecos: lab3
shadowLastChange: 15300
shadowExpire: 16000
shadowMin: 0
shadowWarning: 0
shadowMax: 1000

Please help. I have no clue what to do

---

