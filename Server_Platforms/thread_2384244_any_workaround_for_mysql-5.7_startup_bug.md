---
title: "any workaround for mysql-5.7 startup bug?"
date: 2018-02-04
forum: Server Platforms
---

### Post by pnuke on 2018-02-04
Hello,

Im affected of Bug-1746620, which means mysql-server-5.7 is unable to startup after an pending upgrade on Ubuntu 16.04.3 LTS. The inital problem was with missing apparmor privileges, and now the only error code is "status=2/INVALIDARGUMENT". 

The good thing is, I ran the update on the secondary server first, so the production-system is still the old but working version. But I would like to patch the primary and get the secondary system back online as soon a possible.


Any idea, what could cause this error? Sounds like some config-related issue? But I have no clue, in which config to look first. At this point I hope, not to remove mysql entirely and got through every line of config manually.

---

### Post by LHammonds on 2018-02-04
I don't have a good solution for you but I'd make sure the database structure is up-to-spec by running "mysql_upgrade" which is a good practice for any database that lives through various database software upgrades.

If this is related to app armor and you want your production server patched, you could avoid the issue by uninstalling app armor and then update your system.

LHammonds

---

