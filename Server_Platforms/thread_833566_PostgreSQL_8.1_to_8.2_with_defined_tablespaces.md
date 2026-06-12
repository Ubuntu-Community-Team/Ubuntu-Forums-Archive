---
title: "PostgreSQL 8.1 to 8.2 with defined tablespaces"
date: 2008-06-18
forum: Server Platforms
---

### Post by lavajumper on 2008-06-18
We're trying to upgrade a PostgreSQL 8.1 to 8.2 and we're having some problems getting the cluster upgraded. We use tablespaces to put the datafiles on a disk array and the pg_upgradecluster complains with this:
```

Creating new cluster (configuration: /etc/postgresql/8.2/main, data: /var/lib/postgresql/8.2/main)...
Moving configuration file /var/lib/postgresql/8.2/main/postgresql.conf to /etc/postgresql/8.2/main...
Moving configuration file /var/lib/postgresql/8.2/main/pg_hba.conf to /etc/postgresql/8.2/main...
Moving configuration file /var/lib/postgresql/8.2/main/pg_ident.conf to /etc/postgresql/8.2/main...
Configuring postgresql.conf to use port 5433...
Disabling connections to the old cluster during upgrade...
Disabling connections to the new cluster during upgrade...
Re-enabling connections to the old cluster...
Re-enabling connections to the new cluster...
Creating globals...
ERROR:  directory "/opt/pg/pgdata" is not empty
ERROR:  tablespace "ts_user" does not exist
ERROR:  tablespace "ts_user" does not exist
ERROR:  tablespace "ts_user" does not exist
ERROR:  directory "/tank3/pg/pgdata" is not empty
Fixing hardcoded library paths for stored procedures...


```

At this point it goes on and says its upgrading the databases, but we're so afraid of the errors we interrupt the process(thankfully with no side-effects)

The ts_user tablespace is a populated tablespace, and it is in /opt/pg/pgdata.
/tank3/pg/pgdata is another tablespace(ts_user2).

Does anyone know what needs to be done here? Are these errors normal?

We have backups of the data, so we've considered doing this whole thing "manually"   

Also, does anyone know if extra disk space is needed to perform the upgrade? From the documentation, it appears to create a new full data-set.

Thanks!

---

