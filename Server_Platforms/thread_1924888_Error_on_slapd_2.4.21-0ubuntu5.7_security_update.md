---
title: "Error on slapd 2.4.21-0ubuntu5.7 security update"
date: 2012-02-13
forum: Server Platforms
---

### Post by cybercoke on 2012-02-13
Hi guys, i new from here i a nedd some help on the following error when i do ```
apt-get upgrade -y -t `lsb_release -cs`-security
```:

```
Configurando slapd (2.4.21-0ubuntu5.7) ...
  Backing up /etc/ldap/slapd.conf in /var/backups/slapd-2.4.21-0ubuntu5.6... done.
chown: argumento inválido: ""
dpkg: erro processando slapd (--configure):
 sub-processo script post-installation instalado retornou estado de saída de erro 1
Erros foram encontrados durante o processamento de:
 slapd
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

My [COLOR="Green"]slapd.conf[/COLOR] is:

```
allow bind_v2
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema
include         /etc/ldap/schema/qmail.schema
include         /etc/ldap/schema/samba3.schema

pidfile         /var/run/slapd/slapd.pid
argsfile        /var/run/slapd/slapd.args
loglevel        256
modulepath      /usr/lib/ldap
moduleload      back_hdb
moduleload      syncprov
moduleload      back_monitor
moduleload      back_ldap
sizelimit       3000
tool-threads    1
backend         hdb
database        monitor
database        hdb
suffix          "dc=domain,dc=com,dc=br"
rootdn          "cn=admin,dc=domain,dc=com,dc=br"
rootpw          {SSHA}xxxxxxxxxxxxxxxxxxxxxxxxxxxxx
directory       "/var/lib/ldap"
dbconfig        set_cachesize 0 2097152 0
dbconfig        set_lk_max_objects 1500
dbconfig        set_lk_max_locks 1500
dbconfig        set_lk_max_lockers 1500

index objectClass                       eq,pres
index ou,cn,mail,surname,givenname      eq,pres,sub
index mailAlternateAddress              eq,pres,sub
index uidNumber,gidNumber,loginShell    eq,pres
index uid,memberUid                     eq,pres,sub
index nisMapName,nisMapEntry            eq,pres,sub

lastmod         on
checkpoint      512 30

access to attrs=userPassword,shadowLastChange
        by dn="cn=sync,dc=domain,dc=com,dc=br" read
        by anonymous auth
        by self write
        by * none

access to dn.base="" by * read

access to *
        by dn="cn=admin,dc=domain,dc=br,dc=br" write
        by * read

overlay syncprov
syncprov-checkpoint 100 10
syncprov-sessionlog 100

serverID    1

syncrepl      rid=001
        provider=ldap://www.domain.br
        bindmethod=simple
        binddn="cn=sync,dc=domain,dc=com,dc=br"
        credentials=sk2099
        searchbase="dc=dimas,dc=com,dc=br"
        schemachecking=on
        type=refreshAndPersist
        retry="60 +"

mirrormode on
```


Here is my kernel version: [COLOR="green"]2.6.32-38-server[/COLOR]

I have these error om my master and slave slapd servers.

Thank you.

---

