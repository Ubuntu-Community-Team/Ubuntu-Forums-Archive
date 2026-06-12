---
title: "[SOLVED] ldap replication"
date: 2008-05-28
forum: Server Platforms
---

### Post by cdenley on 2008-05-28
I successfully configured an LDAP server on hardy. Now I am trying to configure it to replicate to a debian etch server. Each has a working ldap server with identical data. However, when I modify anything on the master, I get this error.
```

cdenley@master:~$ sudo ldapadd -v -x -W -c -D "cn=admin,dc=mydomain,dc=com" -f modify.ldif
[sudo] password for cdenley: 
ldap_initialize( <DEFAULT> )
Enter LDAP Password: 
replace loginShell:
	/bin/bash
modifying entry "uid=myuser,ou=people,dc=mydomain,dc=com"
modify complete
ldap_modify: Other (e.g., implementation specific) error (80)

```

This is the format the user data uses
```

dn: uid=myuser,ou=people,dc=mydomain,dc=com
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
uid: myuser
sn: myuser
givenName: myuser
cn: myuser
displayName: myuser
uidNumber: 2006
gidNumber: 2001
userPassword: {SSHA}[my hash]
gecos: myuser
loginShell: /bin/false
homeDirectory: /home/myuser
shadowExpire: -1
shadowFlag: 0
shadowWarning: 7
shadowMin: 8

```

This is the master's slapd.conf
```

cdenley@master:~$ sudo cat /etc/ldap/slapd.conf|grep -v ^#|grep -v "^$"
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema
pidfile         /var/run/slapd/slapd.pid
argsfile        /var/run/slapd/slapd.args
loglevel        none
modulepath	/usr/lib/ldap
moduleload	back_bdb
moduleload	syncprov.la
sizelimit 500
tool-threads 1
backend		bdb
database        bdb
suffix          "dc=mydomain,dc=com"
rootdn          "cn=admin,dc=mydomain,dc=com"
rootpw		{SSHA}[my hash]
directory       "/var/lib/ldap"
dbconfig set_cachesize 0 2097152 0
dbconfig set_lk_max_objects 1500
dbconfig set_lk_max_locks 1500
dbconfig set_lk_max_lockers 1500
index           objectClass,entryCSN,entryUUID eq
overlay syncprov
syncprov-checkpoint 100 10
syncprov-sessionlog 100
lastmod         on
checkpoint      512 30
access to attrs=userPassword,shadowLastChange
        by dn="cn=admin,dc=mydomain,dc=com" write
        by anonymous auth
        by self write
        by * none
access to dn.base="" by * read
access to *
        by dn="cn=admin,dc=mydomain,dc=com" write
        by * read

```

and the slave's...
```

slave:~# cat /etc/ldap/slapd.conf|grep -v ^#|grep -v "^$"
include /etc/ldap/schema/core.schema
include /etc/ldap/schema/cosine.schema
include /etc/ldap/schema/nis.schema
include /etc/ldap/schema/inetorgperson.schema
include /etc/ldap/schema/samba.schema
pidfile         /var/run/slapd/slapd.pid
argsfile        /var/run/slapd/slapd.args
loglevel        0
modulepath	/usr/lib/ldap
moduleload	back_bdb
sizelimit 500
tool-threads 1
backend		bdb
checkpoint 512 30
database        bdb
suffix dc=mydomain,dc=com
rootdn cn=admin,dc=mydomain,dc=com
rootpw {crypt}[my hash]
directory       "/var/lib/ldap"
dbconfig set_cachesize 0 2097152 0
dbconfig set_lk_max_objects 1500
dbconfig set_lk_max_locks 1500
dbconfig set_lk_max_lockers 1500
index           objectClass,entryCSN,entryUUID eq
lastmod         on
syncrepl   rid=1
                provider=ldap://192.168.0.2
                type=refreshOnly
                interval=00:00:00:20
                searchbase="dc=mydomain,dc=com"
                filter="(objectClass=*)"
                attrs="*"
                scope=sub
                schemachecking=off
                updatedn="cn=admin,dc=mydomain,dc=com"
                bindmethod=simple
                binddn="cn=admin,dc=mydomain,dc=com"
                credentials="[my pass]"
updateref       ldap://192.168.0.2
access to attrs=userPassword,shadowLastChange
        by dn="cn=admin,dc=mydomain,dc=com" write
        by anonymous auth
        by self write
        by * none
access to dn.base="" by * read
access to *
        by dn="cn=admin,dc=mydomain,dc=com" write
        by * read

```

What am I doing wrong?

---

### Post by heebus on 2008-05-28
> C.1.14. ldap_add: no structuralObjectClass operational attribute

ldapadd(1) may error:

      adding new entry "uid=XXX,ou=People,o=campus,c=ru"
        ldap_add: Internal (implementation specific) error (80)
           additional info: no structuralObjectClass operational attribute

when slapd(8) cannot determine, based upon the contents of the objectClass attribute, what the structural class of the object should be.

Got this from [this]("http://www.openldap.org/doc/admin24/appendix-common-errors.html") openLDAP page.

---

### Post by cdenley on 2008-05-28
> **heebus said:**
> Got this from [this]("http://www.openldap.org/doc/admin24/appendix-common-errors.html") openLDAP page.
Yeah, I saw that. I didn't get the "additional info", though. Assuming this is the problem, how do I fix it?

---

### Post by heebus on 2008-05-28
This may be a silly question.  Are the two versions of openLDAP the same?

---

### Post by cdenley on 2008-05-28
No. Do they have to be?

---

### Post by heebus on 2008-05-28
They would have to be the same version.

---

### Post by cdenley on 2008-05-28
I just stopped slapd on the slave, and the master still gives me the same problem. This should eliminate incompatibility as the cause, since the master should be able to modify records without the slave. I think it is related to this line in slapd.conf.
```

index objectClass,entryCSN,entryUUID eq

```
If I remove "entryCSN,entryUUID" then the master will update, but the changes don't replicate to the slave. It seemed from what I could find online, those options are necessary for replication.

---

### Post by cdenley on 2008-05-28
I setup slapd on my hardy desktop to act as a slave for testing, in case it needs to be the same version. Same issue, though.

---

### Post by cdenley on 2008-05-29
Does anyone have ldap replication working with hardy? Can you post your configuration? I must be doing something wrong.

---

### Post by cdenley on 2008-05-29
Nevermind. I just replaced
```

index objectClass,entryCSN,entryUUID eq

```
with this
```

index objectClass eq

```
and now both my slaves work, including debian etch with a different version. I'm not sure what changed since last time I tried that, but it's working now.

---

