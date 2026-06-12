---
title: "OpenLDAP Replication per Server Guide - failing at ldapadd"
date: 2011-05-30
forum: Server Platforms
---

### Post by troyready on 2011-05-30
Hello all! I'm in a bit over my head, and would greatly appreciate a pointer or two in the right direction.

I've setup an OpenLDAP server on Ubuntu 10.04 (x64) following the server guide at [https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html) . All the initial configuration went fine, and the server is up and running properly for user authentication and TLS access.

I'd now like to add replication (following the Ubuntu Server Guide's example of a simple provider/consumer model), but something seems to be messed up in my cn=config DIT that's got me totally stuck.

When I attempt to add the ldif file from the guide (Step 4 in LDAP Replication -> Provider Configuration) with the command:

```
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f provider_sync.ldif
```

this is the output I get:

```
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
modifying entry "olcDatabase={1}hdb,cn=config"
ldap_modify: Constraint violation (19)
        additional info: attribute 'olcRootPW' cannot have multiple values

```

Now, I know oldRootPW is not set in the ldif file, so it has to be a misconfiguration in my existing DIT (right?), perhaps something done by Webmin or myself accidentally.

Any help on how to proceed would be greatly appreciated. I imagine that I need to review my server config, but I'm not sure exactly how. I tried to view the cn=config DIT with the following command:

```
ldapsearch -x -H ldap://127.0.0.1:389/ -b cn=config -D cn=admin,dc=myrealdomainhere,dc=com -W
```

But it just returns

```
# extended LDIF
#
# LDAPv3
# base <cn=config> with scope subtree
# filter: (objectclass=*)
# requesting: ALL
#

# search result
search: 2
result: 32 No such object

# numResponses: 1
```

Again, any help would be greatly appreciated!

---

