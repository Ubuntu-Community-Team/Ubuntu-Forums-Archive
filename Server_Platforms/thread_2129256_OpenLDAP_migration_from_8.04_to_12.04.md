---
title: "OpenLDAP migration from 8.04 to 12.04"
date: 2013-03-25
forum: Server Platforms
---

### Post by quad3d@work on 2013-03-25
Anyone done this before and still retains index, logging, and replication functionalities described [here]("https://help.ubuntu.com/12.04/serverguide/openldap-server.html#openldap-server-replication")? I realized the DIT between 8.04 and 12.04 is very different.

If I follow the instructions from [here]("http://supportex.net/2011/02/backup-restore-ldap-database/"), it does some funky stuff and I can't get replication working.

If anyone got any hindsight on how to properly migrate the DIT data over and still retain the functionality of encrypted replication, please let me know.


I was thinking if I slapcat off 8.04 LDAP DB. Manually create the necessary top level OUs and Os on 12.04, modify the LDIF export file to include the CNs and slapadd back.... would this work?

---

### Post by WhaleVPS on 2013-03-26
I'd really copy the two servers over to some kind of test setup then play with it. No matter what you will have massive hassles. If you can get it to work can you please post up here how you did it?

---

