---
title: "Can't find pg_config? PostgreSQL problem"
date: 2009-11-29
forum: Server Platforms
---

### Post by CRCarl on 2009-11-29
All - 
     I installed PostgreSQL using aptitude ie, 
```
sudo aptitude install postgresql postgresql-contrib-8.4
```
 
     The install is working great but I don't I don't think it installed pg_config. It is in a different package? Or have I lost my mind?? Output of find / -name pg* below. Server 9.1 64bit.

```
find / -name pg*
/usr/share/mime/application/pgp-encrypted.xml
/usr/share/mime/application/pgp-keys.xml
/usr/share/mime/application/pgp-signature.xml
/usr/share/man/man8/pg_ctlcluster.8.gz
/usr/share/man/man8/pg_upgradecluster.8.gz
/usr/share/man/man8/pg_dropcluster.8.gz
/usr/share/man/man8/pg_createcluster.8.gz
/usr/share/man/man8/pg_updatedicts.8.gz
/usr/share/man/man1/pg_dumpall.1.gz
/usr/share/man/man1/pg_wrapper.1.gz
/usr/share/man/man1/pg_controldata.1.gz
/usr/share/man/man1/pg.1.gz
/usr/share/man/man1/pg_restore.1.gz
/usr/share/man/man1/pgrep.1.gz
/usr/share/man/man1/pg_resetxlog.1.gz
/usr/share/man/man1/pg_lsclusters.1.gz
/usr/share/man/man1/pg_ctl.1.gz
/usr/share/man/man1/pg_dump.1.gz
/usr/share/postgresql/8.4/pg_hba.conf.sample
/usr/share/postgresql/8.4/contrib/pg_buffercache.sql
/usr/share/postgresql/8.4/contrib/pg_stat_statements.sql
/usr/share/postgresql/8.4/contrib/pg_trgm.sql
/usr/share/postgresql/8.4/contrib/pgxml.sql
/usr/share/postgresql/8.4/contrib/pgcrypto.sql
/usr/share/postgresql/8.4/contrib/pg_freespacemap.sql
/usr/share/postgresql/8.4/contrib/pgstattuple.sql
/usr/share/postgresql/8.4/contrib/pgrowlocks.sql
/usr/share/postgresql/8.4/man/man1/pg_dumpall.1.gz
/usr/share/postgresql/8.4/man/man1/pg_controldata.1.gz
/usr/share/postgresql/8.4/man/man1/pg_restore.1.gz
/usr/share/postgresql/8.4/man/man1/pg_resetxlog.1.gz
/usr/share/postgresql/8.4/man/man1/pg_ctl.1.gz
/usr/share/postgresql/8.4/man/man1/pg_dump.1.gz
/usr/share/postgresql/8.4/pg_ident.conf.sample
/usr/share/postgresql/8.4/pg_service.conf.sample
/usr/share/postgresql-common/pg_wrapper
/usr/share/postgresql-common/pg_checksystem
/usr/lib/postgresql/8.4/lib/pg_stat_statements.so
/usr/lib/postgresql/8.4/lib/pg_trgm.so
/usr/lib/postgresql/8.4/lib/pg_buffercache.so
/usr/lib/postgresql/8.4/lib/pgstattuple.so
/usr/lib/postgresql/8.4/lib/pgrowlocks.so
/usr/lib/postgresql/8.4/lib/pg_freespacemap.so
/usr/lib/postgresql/8.4/lib/pgxml.so
/usr/lib/postgresql/8.4/lib/pgcrypto.so
/usr/lib/postgresql/8.4/bin/pg_controldata
/usr/lib/postgresql/8.4/bin/pg_dumpall
/usr/lib/postgresql/8.4/bin/pgbench
/usr/lib/postgresql/8.4/bin/pg_restore
/usr/lib/postgresql/8.4/bin/pg_resetxlog
/usr/lib/postgresql/8.4/bin/pg_standby
/usr/lib/postgresql/8.4/bin/pg_ctl
/usr/lib/postgresql/8.4/bin/pg_dump
/usr/lib/python2.6/lib2to3/pgen2
/usr/lib/python2.6/lib2to3/pgen2/pgen.py
/usr/lib/python2.6/lib2to3/pgen2/pgen.pyc
/usr/bin/pg_ctlcluster
/usr/bin/pg_dropcluster
/usr/bin/pg
/usr/bin/pg_dumpall
/usr/bin/pg_restore
/usr/bin/pg_upgradecluster
/usr/bin/pg_lsclusters
/usr/bin/pgrep
/usr/bin/pg_dump
/usr/bin/pg_createcluster
/usr/sbin/pg_updatedicts
/etc/postgresql/8.4/main/pg_ctl.conf
/etc/postgresql/8.4/main/pg_ident.conf
/etc/postgresql/8.4/main/pg_hba.conf
/etc/postgresql-common/pg_upgradecluster.d
/etc/alternatives/pg_dumpall.1.gz
/etc/alternatives/pg_controldata.1.gz
/etc/alternatives/pg_restore.1.gz
/etc/alternatives/pg_resetxlog.1.gz
/etc/alternatives/pg_ctl.1.gz
/etc/alternatives/pg_dump.1.gz
/var/cache/man/cat1/pg.1.gz
/var/lib/postgresql/8.4/main/global/pg_control
/var/lib/postgresql/8.4/main/global/pg_database
/var/lib/postgresql/8.4/main/global/pg_auth
/var/lib/postgresql/8.4/main/pg_twophase
/var/lib/postgresql/8.4/main/pg_xlog
/var/lib/postgresql/8.4/main/pg_tblspc
/var/lib/postgresql/8.4/main/pg_multixact
/var/lib/postgresql/8.4/main/pg_clog
/var/lib/postgresql/8.4/main/pg_subtrans
/var/lib/postgresql/8.4/main/pg_stat_tmp
/var/lib/postgresql/8.4/main/pg_stat_tmp/pgstat.stat
/var/lib/postgresql/8.4/main/base/16386/pg_internal.init
/var/lib/postgresql/8.4/main/base/11564/pg_internal.init
/var/lib/postgresql/8.4/main/base/16384/pg_internal.init
/var/lib/postgresql/8.4/main/base/16385/pg_internal.init
/var/lib/postgresql/8.4/main/base/1/pg_internal.init

```

---

### Post by Bachstelze on 2009-11-30
/usr/bin/pg_config is in the package libpq-dev.

---

### Post by SabreWolfy on 2009-11-30
> **Bachstelze said:**
> /usr/bin/pg_config is in the package libpq-dev.

Thanks :-)

---

### Post by alanhaggai on 2010-02-16
Thank you. :-)

---

### Post by vinibdr on 2010-08-12
I typed this command sudo apt-get install libpq-dev and the problem got fixed.

My system did not have the liqpq-dev library installed.

---

### Post by maxniko on 2011-04-11
Thank you very much. That solved it!

---

### Post by bishop__ on 2011-12-13
I was installing perl DBD::Pg module and it was asking for pg_config path ... I that that it was asking for postgresql configuration path. LOL. 

Thanks! My problem fixed! :)



--
[Ubuntu Philippines]("http://www.rommellaranjo.com")

---

