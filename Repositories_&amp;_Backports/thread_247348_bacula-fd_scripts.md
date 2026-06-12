---
title: "bacula-fd scripts"
date: 2006-08-30
forum: Repositories &amp; Backports
---

### Post by swinnea on 2006-08-30
I've been working with bacula getting a backup system working.  One of the errors when catalog backups run is that scripts in /etc/bacula/scripts are missing.

in the package bacula-fd there are four files listed in the package
make_catalog_backup
delete_catalog_backup
startmysql
stopmysql


These don't seem to actually be copied into the /etc/bacula/scripts directory.  I'm not sure if they are actually in the bacula-fd package.

I was able to find them in the debian depository in the bacula-fd package and copy them manually into the scripts directory.

---

