---
title: "slapd/OpenLDAP uidNumber Generation"
date: 2017-08-03
forum: Server Platforms
---

### Post by CharlesT423 on 2017-08-03
Hi Everyone,

  I'm trying to setup phpldapadmin with slapd on Ubuntu 16.04 and I can't get the uidNumber/gidNumber pool to work.  The only documentation I can find anywhere on this subject says to add the following to your LDAP schema:
```
objectclass ( 1.3.6.1.4.1.7165.1.2.2.3 NAME 'uidPool' SUP top AUXILIARY
       DESC 'Pool for allocating UNIX uids'
       MUST ( uidNumber $ cn ) )

objectclass ( 1.3.6.1.4.1.7165.1.2.2.4 NAME 'gidPool' SUP top AUXILIARY
       DESC 'Pool for allocating UNIX gids'
       MUST ( gidNumber $ cn ) )

```
Unfortunately, there is no documentation on *how* to add that to your schema, and the standard ```
ldapadd -Y EXTERNAL -H ldapi:/// -f idPools.diff
``` doesn't work (gives an "invalid format" error.)

Does anyone know how to add those two vars to the server?

---

