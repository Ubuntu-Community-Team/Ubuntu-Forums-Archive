---
title: "Botched PostgreSQL installation"
date: 2011-10-16
forum: Server Platforms
---

### Post by WhatsInANick on 2011-10-16
I am running the latest version of ubuntu 11.10 (Oneiric).

I tried installing PostgreSQL with:

```
apt-get install postgresql
```

There are however no files added to my system:

There are no config files and the folder /etc/postgresql/ des not exists.
The only postgresql related folder in /etc/ is /etc/postgresql-common

I also can't start pg with /etc/init.d/postgresql, and status returns back nothing.

when i run locate postgresql I only get som apt caches and docs but no executables or shared libs:

```
$ locate postgresql
/etc/postgresql-common
/etc/bash_completion.d/postgresql
/etc/init.d/postgresql
/etc/logrotate.d/postgresql-common
/etc/postgresql-common/pg_upgradecluster.d
/etc/postgresql-common/root.crt
/etc/postgresql-common/user_clusters
/etc/rc0.d/K21postgresql
/etc/rc1.d/K21postgresql
/etc/rc2.d/S19postgresql
/etc/rc3.d/S19postgresql
/etc/rc4.d/S19postgresql
/etc/rc5.d/S19postgresql
/etc/rc6.d/K21postgresql
/etc/sysctl.d/30-postgresql-shm.conf
/root/debian/postgresql-9.1.install
/root/debian/postgresql-9.1.links
/root/debian/postgresql-9.1.postinst
/root/debian/postgresql-9.1.postrm
/root/debian/postgresql-9.1.preinst
/root/debian/postgresql-9.1.prerm
/root/debian/postgresql-client-9.1.install
/root/debian/postgresql-client-9.1.postinst
/root/debian/postgresql-client-9.1.prerm
/root/debian/postgresql-contrib-9.1.install
/root/debian/postgresql-contrib-9.1.postinst
/root/debian/postgresql-contrib-9.1.prerm
/root/debian/postgresql-doc-9.1.dirs
/root/debian/postgresql-doc-9.1.doc-base
/root/debian/postgresql-doc-9.1.install
/root/debian/postgresql-plperl-9.1.install
/root/debian/postgresql-plpython-9.1.install
/root/debian/postgresql-pltcl-9.1.install
/root/debian/postgresql-server-dev-9.1.install
/usr/lib/postgresql
/usr/lib/postgresql/8.4
/usr/share/postgresql
/usr/share/postgresql-common
/usr/share/doc/postgresql
/usr/share/doc/postgresql-8.4
/usr/share/doc/postgresql-client-8.4
/usr/share/doc/postgresql-client-common
/usr/share/doc/postgresql-common
/usr/share/doc/postgresql/README
/usr/share/doc/postgresql/changelog.Debian.gz
/usr/share/doc/postgresql/copyright
/usr/share/doc/postgresql-client-common/TODO
/usr/share/doc/postgresql-client-common/changelog.gz
/usr/share/doc/postgresql-client-common/copyright
/usr/share/doc/postgresql-common/README.Debian.gz
/usr/share/doc/postgresql-common/README.Devel
/usr/share/doc/postgresql-common/TODO
/usr/share/doc/postgresql-common/architecture.html
/usr/share/doc/postgresql-common/changelog.gz
/usr/share/doc/postgresql-common/copyright
/usr/share/lintian/overrides/postgresql-client-common
/usr/share/lintian/overrides/postgresql-common
/usr/share/man/man5/postgresqlrc.5.gz
/usr/share/man/man7/postgresql-common.7.gz
/usr/share/postgresql/8.4
/usr/share/postgresql-common/PgCommon.pm
/usr/share/postgresql-common/init.d-functions
/usr/share/postgresql-common/maintscripts-functions
/usr/share/postgresql-common/pg_checksystem
/usr/share/postgresql-common/pg_wrapper
/usr/share/postgresql-common/run-upgrade-scripts
/usr/share/postgresql-common/supported-versions
/usr/share/postgresql-common/t
/usr/share/postgresql-common/testsuite
/usr/share/postgresql-common/upgrade-scripts
/usr/share/postgresql-common/t/001_packages.t
/usr/share/postgresql-common/t/002_existing_clusters.t
/usr/share/postgresql-common/t/005_PgCommon.t
/usr/share/postgresql-common/t/010_defaultport_cluster.t
/usr/share/postgresql-common/t/020_create_sql_remove.t
/usr/share/postgresql-common/t/030_errors.t
/usr/share/postgresql-common/t/040_upgrade.t
/usr/share/postgresql-common/t/041_upgrade_custompaths.t
/usr/share/postgresql-common/t/042_upgrade_tablespaces.t
/usr/share/postgresql-common/t/050_encodings.t
/usr/share/postgresql-common/t/051_inconsistent_encoding_upgrade.t
/usr/share/postgresql-common/t/052_upgrade_encodings.t
/usr/share/postgresql-common/t/060_obsolete_confparams.t
/usr/share/postgresql-common/t/070_non_postgres_clusters.t
/usr/share/postgresql-common/t/080_start.conf.t
/usr/share/postgresql-common/t/085_pg_ctl.conf.t
/usr/share/postgresql-common/t/090_multicluster.t
/usr/share/postgresql-common/t/100_upgrade_scripts.t
/usr/share/postgresql-common/t/110_integrate_cluster.t
/usr/share/postgresql-common/t/120_pg_upgradecluster_scripts.t
/usr/share/postgresql-common/t/130_nonroot_admin.t
/usr/share/postgresql-common/t/140_pg_config.t
/usr/share/postgresql-common/t/150_tsearch_stemming.t
/usr/share/postgresql-common/t/TestLib.pm
/usr/share/postgresql-common/t/template
/usr/share/postgresql-common/upgrade-scripts/SPECIFICATION
/var/cache/postgresql
/var/cache/apt/archives/postgresql-8.4_8.4.8-0ubuntu0.11.04_amd64.deb
/var/cache/apt/archives/postgresql-8.4_8.4.9-0ubuntu0.11.04_amd64.deb
/var/cache/apt/archives/postgresql-client-8.4_8.4.8-0ubuntu0.11.04_amd64.deb
/var/cache/apt/archives/postgresql-client-8.4_8.4.9-0ubuntu0.11.04_amd64.deb
/var/cache/apt/archives/postgresql-client-common_114_all.deb
/var/cache/apt/archives/postgresql-client_8.4.9-0ubuntu0.11.04_all.deb
/var/cache/apt/archives/postgresql-common_114_all.deb
/var/cache/apt/archives/postgresql-contrib-8.4_8.4.9-0ubuntu0.11.04_amd64.deb
/var/cache/apt/archives/postgresql-contrib_8.4.9-0ubuntu0.11.04_all.deb
/var/cache/apt/archives/postgresql_8.4.8-0ubuntu0.11.04_all.deb
/var/cache/apt/archives/postgresql_8.4.9-0ubuntu0.11.04_all.deb
/var/cache/postgresql/dicts
/var/lib/postgresql
/var/lib/dpkg/info/postgresql-8.4.list
/var/lib/dpkg/info/postgresql-8.4.md5sums
/var/lib/dpkg/info/postgresql-8.4.postinst
/var/lib/dpkg/info/postgresql-8.4.postrm
/var/lib/dpkg/info/postgresql-8.4.preinst
/var/lib/dpkg/info/postgresql-8.4.prerm
/var/lib/dpkg/info/postgresql-client-8.4.list
/var/lib/dpkg/info/postgresql-client-8.4.md5sums
/var/lib/dpkg/info/postgresql-client-8.4.postinst
/var/lib/dpkg/info/postgresql-client-8.4.prerm
/var/lib/dpkg/info/postgresql-client-common.conffiles
/var/lib/dpkg/info/postgresql-client-common.list
/var/lib/dpkg/info/postgresql-client-common.md5sums
/var/lib/dpkg/info/postgresql-client-common.postrm
/var/lib/dpkg/info/postgresql-common.conffiles
/var/lib/dpkg/info/postgresql-common.config
/var/lib/dpkg/info/postgresql-common.list
/var/lib/dpkg/info/postgresql-common.md5sums
/var/lib/dpkg/info/postgresql-common.postinst
/var/lib/dpkg/info/postgresql-common.postrm
/var/lib/dpkg/info/postgresql-common.preinst
/var/lib/dpkg/info/postgresql-common.prerm
/var/lib/dpkg/info/postgresql-common.templates
/var/lib/dpkg/info/postgresql-common.triggers
/var/lib/dpkg/info/postgresql.list
/var/lib/dpkg/info/postgresql.md5sums
/var/lib/update-rc.d/postgresql
/var/log/postgresql
```

I do have the following progrmas in my path:

```

pg                 pg_ctlcluster      pg_dumpall         pg_restore
pg_config          pg_dropcluster     pg_lsclusters      pg_updatedicts
pg_createcluster   pg_dump            pgrep              pg_upgradecluster

```

I tried purging postgresql and reinstalling it but this gives the same result.

What is preventing pg to be installed correctly?

---

### Post by jgrocha on 2011-10-16
Please do the following command, to see what packages related to postgresql are installed:

dpkg -l | grep postgres

and report us back the output.

---

### Post by WhatsInANick on 2011-10-16
right back atcha

```
$ dpkg -l | grep postgres
ii  postgresql                       9.1+122ubuntu1                          object-relational SQL database (supported version)
rc  postgresql-8.4                   8.4.9-0ubuntu0.11.04                    object-relational SQL database, version 8.4 server
ii  postgresql-9.1                   9.1.1-1                                 object-relational SQL database, version 9.1 server
ii  postgresql-9.1-postgis           1.5.3-1                                 Geographic objects support for PostgreSQL 9.1
ii  postgresql-client-9.1            9.1.1-1                                 front-end programs for PostgreSQL 9.1
ii  postgresql-client-common         122ubuntu1                              manager for multiple PostgreSQL client versions
ii  postgresql-common                122ubuntu1                              PostgreSQL database-cluster manager
ii  postgresql-contrib               9.1+122ubuntu1                          additional facilities for PostgreSQL (supported version)
ii  postgresql-contrib-9.1           9.1.1-1                                 additional facilities for PostgreSQL
```

---

### Post by rafaelss on 2011-10-19
I'm with the same problem

```
$:~# dpkg -l | grep postgres
ii  postgresql                       9.1+122ubuntu1                          object-relational SQL database (supported version)
ii  postgresql-9.1                   9.1.1-1                                 object-relational SQL database, version 9.1 server
ii  postgresql-client-9.1            9.1.1-1                                 front-end programs for PostgreSQL 9.1
ii  postgresql-client-common         122ubuntu1                              manager for multiple PostgreSQL client versions
ii  postgresql-common                122ubuntu1                              PostgreSQL database-cluster manager
ii  postgresql-contrib               9.1+122ubuntu1                          additional facilities for PostgreSQL (supported version)
ii  postgresql-contrib-9.1           9.1.1-1                                 additional facilities for PostgreSQL
ii  postgresql-server-dev-9.1        9.1.1-1                                 development files for PostgreSQL 9.1 server-side programming
```

---

### Post by SeijiSensei on 2011-10-19
> **WhatsInANick said:**
> I also can't start pg with /etc/init.d/postgresql, and status returns back nothing.

PostgreSQL is packaged to use the newer [Upstart]("http://upstart.ubuntu.com/") method for managing daemons.  Try "sudo service postgresql restart" and see what happens.

> What is preventing pg to be installed correctly?

Try deleting your 8.4 installation.  In fact I'd remove both 8.4 and 9.1 and start over with just 9.1.  Make sure you've dumped your 8.4 databases with pg_dump first.

```
sudo apt-get purge postgresql-9.1
sudo apt-get purge postgresql-9.1*
sudo apt-get purge postgresql-8.4
sudo apt-get purge postgresql-8.4*
sudo apt-get install postgresql-9.1
sudo apt-get install postgresql-client-9.1
```

> **rafaelss said:**
> I'm with the same problem

The "same problem" is a bit vague, I'm afraid.  Did you try starting postgresql-9.1 with the "service" command?

---

### Post by rafaelss on 2011-10-19
I did, nothing happens.

```
$:~# service postgresql start
$:~# 
```

Looking at /usr/share/postgresql-common/init.d-functions file, specifically at line 12, it's checking for /etc/postgresql directory, that doesn't exist. here is the line 12

```
[ -d "/etc/postgresql/$2" ] || return 0
```

Looks like some steps are missing or something like that in the installation process.

---

### Post by SeijiSensei on 2011-10-19
I created a VirtualBox VM and installed a fresh copy of Kubuntu 11.10 into it. (I doubt the desktop environment matters when it comes to running PostgreSQL.) After the computer rebooted, I ran

```
sudo apt-get install postgresql-9.1
```

Ubuntu installed both the server and the client.  When the installer finished, I could run 

```
sudo service postgresql stop
sudo service postgresql start
```

and have both steps complete correctly.  I then tested that I could connect with the client to the default "template1" database as user "postgres" like this:

```
sudo su postgres -c 'psql -U postgres template1'
```

I got the psql prompt as expected.

Is your installation an upgrade or from the CDROM?

---

### Post by rafaelss on 2011-10-19
I'm setting up a linode instance.
Anyway, after 4 tries, everything is working fine. I really don't know what happened.

I don't know if I miss some steps earlier, but what I did this time was:

- install build-essential
- configure locales
- configure tzdata
- install libpq-dev
- configure hostname
- install nginx
- disable root ssh login
- create an user

---

### Post by WhatsInANick on 2011-10-23
I think that there was a conflict in the installation that in installed all files but somehow skipped the config files (those in /etc/). I just did a purge of everythong pg related and now it works.

---

### Post by realmac on 2012-11-10
> **rafaelss said:**
> I'm setting up a linode instance.
Anyway, after 4 tries, everything is working fine. I really don't know what happened.

I don't know if I miss some steps earlier, but what I did this time was:

- install build-essential
- configure locales
- configure tzdata
- install libpq-dev
- configure hostname
- install nginx
- disable root ssh login
- create an user

I had a similar problem and it was the locales that were the cause. When I tried to install Postgres a lot of the files just weren't there. I was getting a locale issue prior to my postgres install and when I ran

```

sudo locale-gen en_CA en_CA.UTF-8
sudo dpkg-reconfigure locales

```
it fixed the locales issue. Afterwards Postgres installed properly with apt-get install postgresql.

---

### Post by howefield on 2012-11-12
Thanks for the extra information.

Thread closed.

---

