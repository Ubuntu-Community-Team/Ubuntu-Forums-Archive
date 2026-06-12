---
title: "bacula script problems"
date: 2008-06-18
forum: Server Platforms
---

### Post by jujitsu-nut on 2008-06-18
Hi.

Not sure if this is the right forum or not...

I have been testing bacula on Ubuntu 8.04 LTS and running the BackupCatalog job. It fails on the RunBefore: section of bacula-dir.conf where it tries to create a bacula.sql mysql dump and reads the username, db name and password from /var/lib/bacula.my.cnf

The problem is there is no /var/lib/bacula/.my.cnf file so no bacula.sql is created and therefore the BackupCatalog job fails.

Has anyone seen this before and if so, what is the fix?

Thanks in advance.

---

### Post by jujitsu-nut on 2008-06-19
It turns this has been a bug in the awk script since at least bacula ver. 2.2.8. I have not figured out how to resolve it but somehow I have to get the script to be run as the bacula user.

It's funny how difficult Bacula is to set up and learn but at the same time, once you get used to it, it's actually easy.

---

