---
title: "LDAP password policy"
date: 2011-04-08
forum: Server Platforms
---

### Post by eknuds on 2011-04-08
I'm trying to add a password policy into OpenLDAP 2.4 on 10.04 and it's driving me out of my mind.
I keep getting this error:
root@www:/etc/ldap# sudo ldapadd -x -D cn=God,dc=example,dc=org -W -f ppolicy.ldif 
Enter LDAP Password: 
adding new entry "cn=default,ou=policies,dc=example,dc=org"
ldap_add: Invalid syntax (21)
	additional info: objectClass: value #0 invalid per syntax

My slapd.conf has the relevant sections:
```

#
# See slapd.conf(5) for details on configuration options.
# This file should NOT be world readable.
#
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/inetorgperson.schema
include         /etc/ldap/schema/rfc2307bis.schema
include         /etc/ldap/schema/dnszone.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/2739.schema
include         /etc/ldap/schema/ppolicy.schema

# Define global ACLs to disable default read access.

# Do not enable referrals until AFTER you have a working directory
# service AND an understanding of referrals.
#referral       ldap://root.openldap.org

pidfile         /var/run/slapd/slapd.pid
argsfile        /var/run/slapd/slapd.args

# Load dynamic backend modules:
modulepath      /usr/lib/ldap/modules
# moduleload    back_ldap.la
# moduleload    back_meta.la
 moduleload    back_monitor.la
# moduleload    back_perl.la
moduleload      ppolicy.la

database bdb
suffix "dc=example,dc=org"
rootdn "cn=God,dc=example,dc=org"
rootpw {SSHA}pYfvWVDrSo+whJosTLtrJKKitZ5LdBaO
directory /var/lib/ldap/
checkpoint 1024 5
cachesize 10000
index objectClass,uidNumber,gidNumber eq
index member,mail eq,pres
index cn,displayname,uid,sn,givenname sub,eq,pres
overlay ppolicy
ppolicy_default "cn=default,ou=policies,dc=example,dc=org"


```


The ldif.  The container is successfully added:
```

dn: ou=policies,dc=example,dc=org
objectClass: organizationalUnit
objectClass: top
ou: policies

dn: cn=default,ou=policies,dc=example,dc=org
cn: default
objectClass: pwdPolicy
objectClass: person
objectClass: top
pwdAllowUserChange: TRUE
pwdAttribute: userPassword
pwdCheckQuality: 2
pwdExpireWarning: 600
pwdFailureCountInterval: 30
pwdGraceAuthNLimit: 5
pwdInHistory: 5
pwdLockout: TRUE
pwdLockoutDuration: 0
pwdMaxAge: 0
pwdMaxFailure: 5
pwdMinAge: 0
pwdMinLength: 5
pwdMustChange: FALSE
pwdSafeModify: FALSE
sn: PPolicy

```

](*,)

---

### Post by eknuds on 2011-04-08
Figured out that it has to do with the dynamic backend.  What's the right way to add the ppolicy schema to the backend db?

---

### Post by eknuds on 2011-04-09
So I finally figured out how to add the ppolicy schema to the backend with [with this howto](http://www.linuxquestions.org/questions/linux-server-73/how-to-add-a-new-schema-to-openldap-2-4-11-a-700452/).
But now it tells me it doesn't know what to do with the OID?
```

root@www:/etc/ldap/schema# sudo ldapadd -x -D cn=God,dc=example,dc=org -W -f ../ppolicy.ldif 
Enter LDAP Password: 
adding new entry "cn=default,ou=policies,dc=example,dc=org"
ldap_add: Invalid syntax (21)
	additional info: pwdAttribute: value #0 invalid per syntax


```

---

### Post by eknuds on 2011-04-09
It turns out that the schema.ldif that Ubuntu puts into slapd.d is basically empty and it gives me an error when I try to put in one with some data in it.  Not only that it prevents me from deleting the original:
```

root@www:/etc/ldap# sudo ldapadd -x -D cn=God,dc=example,dc=org -W -f ./convert/cn\=config/cn\=schema.ldif
Enter LDAP Password: 
adding new entry "cn=schema,cn=config"
ldap_add: Insufficient access (50)


```

---

