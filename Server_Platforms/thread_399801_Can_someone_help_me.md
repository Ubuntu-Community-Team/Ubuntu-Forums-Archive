---
title: "Can someone help me ?"
date: 2007-04-02
forum: Server Platforms
---

### Post by James0591 on 2007-04-02
ok here is my problem ```
sudo apt-get install postgresql-client-8.1
Reading package lists... Done
Building dependency tree... Done
postgresql-client-8.1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 43 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up gforge-db-postgresql (3.1-31) ...
Configuring for PostgreSQL 7.3 or later
cat: /etc/postgresql/pg_hba.conf.gforge-new: Is a directory
dpkg: error processing gforge-db-postgresql (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gforge-ldap-openldap:
 gforge-ldap-openldap depends on gforge-db-postgresql | gforge-db; however:
  Package gforge-db-postgresql is not configured yet.
  Package gforge-db is not installed.
  Package gforge-db-postgresql which provides gforge-db is not configured yet.
dpkg: error processing gforge-ldap-openldap (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gforge-ftp-proftpd:
 gforge-ftp-proftpd depends on gforge-ldap-openldap | gforge-ldap; however:
  Package gforge-ldap-openldap is not configured yet.
  Package gforge-ldap is not installed.
  Package gforge-ldap-openldap which provides gforge-ldap is not configured yet.dpkg: error processing gforge-ftp-proftpd (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gforge-db-postgresql
 gforge-ldap-openldap
 gforge-ftp-proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

how can i fix this ? I am following this guide , it is a bit out dated though 
[http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06)

Also while installing proftpd it came up with this

```
The PostgreSQL version 7.4 is obsolete, but you still have the server and/or client package installed. Please install the latest packages (postgresql-8.1 and postgresql-client-8.1) and upgrade your existing  clusters with pg_upgradecluster (see manpage).

Please be aware that the installation of postgresql-8.1 will automatically create a default cluster 8.1/main. If you want to upgrade the 7.4/main cluster, you need to remove the already existing 8.1 cluster (pg_dropcluster --stop 8.1 main, see manpage for details).

The old server and client packages are not supported any more. After having upgraded the existing clusters, you should remove the postgresql-7.4 and postgresql-client-7.4 packages.
```

how do i do this ?

---

### Post by aysiu on 2007-04-02
Dependency problems usually stem from conflicting repositories.

[Get a fresh sources.list](http://www.psychocats.net/ubuntu/sources), do a ```
sudo apt-get update
``` and then try again.

---

