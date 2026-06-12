---
title: "Ldap ldapadd doesn't want to login"
date: 2006-08-28
forum: Server Platforms
---

### Post by latz-twn on 2006-08-28
Hi there,

I started building a ldap active directory, to enable logins through ssh, ftp, web, and samba beeing authenticated by the ldap directory. Now I am all ready to start off populating the database, but for some reason ldap doesn't accept my password. 

**slapd.conf**
```

#######################################################################
# Global Directives:

allow bind_v2

# Schema and objectClass definitions
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema
include         /etc/ldap/schema/misc.schema
#include         /etc/ldap/schema/postfix.schema
#include         /etc/ldap/schema/samba.schema

schemacheck on
pidfile         /var/run/slapd/slapd.pid
argsfile        /var/run/slapd/slapd.args
modulepath      /usr/lib/ldap
moduleload      back_bdb


# Permission and rights
access to attrs=userPassword
        by dn="uid=root,ou=People,dc=ix,dc=net" write
        by dn="cn=Manager,dc=ix,dc=net" write
        by anonymous auth
        by self write
        by * none

access to dn.base="" by * read

access to *
         by dn="cn=Manager,dc=ix,dc=net" write
         by * read


# Database settings
backend         bdb
database        bdb
suffix          "dc=ix,dc=net"
rootdn          "cn=Manager,dc=ix,dc=net"
rootpw          secret
directory       /var/lib/ldap
index   objectClass     eq
lastmod         on

```


So what I did afterwords was generating ldif, for the shadow,passwd and group files. Using the migration tools that can be found [here](http://www.padl.com/OSS/MigrationTools.html). Now when I try to add those ldif's to the ldap directory I get this error.

```

root@phynix:/tmp# ldapadd -D "cn=Manager,dc=ix,dc=net" -W -f /tmp/base.ldif
Enter LDAP Password:
SASL/DIGEST-MD5 authentication started
ldap_sasl_interactive_bind_s: Internal (implementation specific) error (80)
        additional info: SASL(-13): user not found: no secret in database

```


Any idea? Cheers for your help already!

---

### Post by gpredrag on 2006-08-28
ldap tools asume that you like to use SASL authentication. If you didn' set sasl authentication in the first place, you are probably trying to bind using simple authentication. Resolutions:
1) use -x in that command to use simple authentication. If you are doing it accross the network you should be using TLS
2) Arrange for SASL authentication, see docs on openLDAP admin guide. That way your password would be kept in sasldb database.

---

### Post by latz-twn on 2006-08-28
Alrighty then! Thx a lot for your help! :)

I am just about to build the ldap database, so there is no need for TLS just right now.

---

