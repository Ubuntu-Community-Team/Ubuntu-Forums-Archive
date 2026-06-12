---
title: "Ldap freeze and users can't connect"
date: 2013-02-06
forum: Server Platforms
---

### Post by TUXIFI on 2013-02-06
Hi,

I ve got a problem with my ldap network server,
when they are near from 40 people connected 
the slapd server can't respond to others andi need to restart it to solve that.

Is it a cache problem? The load average is near 0.6 all the time
On this server i put an nfsd server too


```
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema
include         /etc/ldap/schema/samba.schema

include         /etc/ldap/schema/autofs.schema
include         /etc/ldap/schema/cri.schema
include         /etc/ldap/schema/internet2.schema
include         /etc/ldap/schema/supann.schema
include         /etc/ldap/schema/ustl.schema
include         /etc/ldap/schema/rfc2739.schema

pidfile         /var/run/slapd/slapd.pid
argsfile        /var/run/slapd/slapd.args

loglevel        110
logfile /var/log/slapd.log


modulepath      /usr/lib/ldap
moduleload      back_hdb

#sizelimit 2500

tool-threads 1

backend         hdb
database        hdb

suffix          "dc=test,dc=priv,dc=univ,dc=fr"
rootdn          "cn=admin,dc=test,dc=priv,dc=univ,dc=fr"
rootpw {SSHA}XXXXXXXXXXXXXXXXXXXXxxxx
directory       "/var/lib/ldap"


cachesize       100000
#dbconfig set_cachesize 0 4097152 0

#idbconfig set_lk_max_objects 1500
modulepath      /usr/lib/ldap
moduleload      back_hdb

#sizelimit 2500

tool-threads 1

backend         hdb
database        hdb

suffix          "dc=test,dc=priv,dc=univ,dc=fr"
rootdn          "cn=admin,dc=test,dc=priv,dc=univ,dc=fr"
rootpw {SSHA}XXXXXXXXXXXXXXXXXXXX
directory       "/var/lib/ldap"


cachesize       100000
#dbconfig set_cachesize 0 4097152 0

#idbconfig set_lk_max_objects 1500
#dbconfig set_lk_max_locks 1500
#dbconfig set_lk_max_lockers 1500

index objectClass           eq
index cn                    pres,sub,eq
index sn                    pres,sub,eq
index uid                   pres,sub,eq
index displayName           pres,sub,eq
index uidNumber             eq
index uniqueMember          eq
index gidNumber             eq
index memberUID             eq
index sambaSID              eq
index sambaPrimaryGroupSID  eq
index sambaDomainName       eq
index default               sub

#lastmod         on

access to attrs=userPassword,shadowLastChange
        by dn.regex="cn=admin,dc=test,dc=priv,dc=univ,dc=fr" write
        by anonymous auth
        by self write
        by * none

access to *
        by dn.regex="cn=admin,dc=test,dc=priv,dc=univ,dc=fr" write
        by * read




```

---

