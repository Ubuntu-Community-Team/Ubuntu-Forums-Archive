---
title: "ldap_bind: Invalid credentials (49) error"
date: 2005-08-15
forum: Server Platforms
---

### Post by Myles3 on 2005-08-15
I am installed LDAP a while ago to work with OpenXchange but each time I try to add a user it gives me this error
```
ldap_bind: Invalid credentials (49)
```

This is my /etc/ldap/slapd file:
```
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema
include         /etc/ldap/schema/java.schema
include         /etc/ldap/schema/openldap.schema

# edit location of openxchange.schema
include         /usr/local/openxchange/share/openxchange.schema

modulepath      /usr/lib/ldap
moduleload      back_bdb
#moduleload     back_ldap
moduleload      back_ldbm
moduleload      back_passwd
moduleload      back_shell

loglevel 4

# following did not work with my openLDAP-2.0 so I commented it out
#allow bind_v2

pidfile         /var/run/slapd.pid
database        bdb
suffix          "dc=example,dc=org"
rootdn          "uid=mailadmin,dc=example,dc=org"
rootpw          unknown
directory       /var/lib/ldap
index           uid,mailEnabled,cn,sn,givenname,lnetMailAccess,alias,loginDestination eq,sub
``` 

and this is my /etc/ldap/ldap.conf file which is used to connect to the server.
```
BASE dc=example,dc=org
HOST localhost
```

---

### Post by 4ziz on 2008-07-09
strange, this is old bug but I'm still getting error like this on ubuntu-8.04. after stuck on a few hours, finally i can fix this.

run this:
....
rm -rf /var/backups/unknown-2.4.7-6ubuntu2.ldapdb
dpkg-reconfigure slapd
/etc/init.d/slapd restart

as the instruction on [http://www.debuntu.org/ldap-server-and-linux-ldap-clients:](http://www.debuntu.org/ldap-server-and-linux-ldap-clients:) then I re-run:

ldapadd -x -W -D "cn=admin,dc=debuntu,dc=local" -f ~/people_group.ldif
ldapadd -x -W -D "cn=admin,dc=debuntu,dc=local" -f ~/group.ldif
ldapadd -x -W -D "cn=admin,dc=debuntu,dc=local" -f ~/passwd.ldif

---

