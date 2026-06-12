---
title: "Can't authenticate against slave openldap server after replication"
date: 2020-03-10
forum: Server Platforms
---

### Post by melvin2345 on 2020-03-10
I have 2 openldap servers, one serving as master, one serving as slave. I can authenticate just fine to the master server with ldapsearch, but after successfully replicating, on the slave ldapsearch only works for the admin account, but none of the user accounts. if I do slapcat I can see that all of the accounts replicated, and adding new users to the master replicates just fine too. The ldapsearch string I used to successfully test on master I copied directly to the slave, replacing the value for -H

I'm not even sure where to start looking for how to fix this, just looking for a nudge in the right direction.

---

