---
title: "Ubuntu 10.04 LDAP Replication - please help"
date: 2011-04-18
forum: Server Platforms
---

### Post by StutteringJohnSmith on 2011-04-18
Ubuntu 10.04 LDAP Replication - please help

I was trying to setup LDAP Replication following:
[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html#openldap-server-installation](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html#openldap-server-installation)

but I put the wrong IP address in the consumer_sync.ldif file and now I  am trying to fix it but I am getting the following error;  please help  me out!


jsmith@s2rweb2:/var/nfs$ sudo ldapadd -c -Y EXTERNAL -H ldapi:/// -f consumer_sync.ldif
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
modifying entry "cn=module{0},cn=config"
ldap_modify: Type or value exists (20)
    additional info: modify/add: olcModuleLoad: value #0 already exists

modifying entry "olcDatabase={1}hdb,cn=config"
ldap_modify: Type or value exists (20)
    additional info: modify/add: olcDbIndex: value #0 already exists

---

