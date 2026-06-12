---
title: "Upgrade Postgresql 9.1 to 9.2"
date: 2013-07-16
forum: Server Platforms
---

### Post by mbnoimi on 2013-07-16
I want to upgrade my Postgresql server from 9.1 to 9.2 but when I did the following ubuntu created a new server instead of upgrading Potsgresql & migrating the old data!

```
sudo add-apt-repository ppa:pitti/postgresql
sudo apt-get update
sudo apt-get install postgresql-9.2 
sudo apt-get upgrade
```

P.S. I forced to use Pg 9.2 because I want to use some feature not available in 9.1

---

### Post by SeijiSensei on 2013-07-16
When I last tried this, I believe it left the 9.1 installation intact.  If so, here's one solution.

Stop the 9.2 server and start the 9.1 one instead.  Then use pg_dumpall to create a plain-text backup of the database(s).  (Once you get everything running, you should create a script running from cron that does this at least once a day.)  Now stop the 9.1 server, start the 9.2 server, and feed the dump into the server with psql < /path/to/dumpfile.  You'll need to become the postgres user to do this easily by first running:

```

sudo su
[enter password]
su postgres

```

---

### Post by mbnoimi on 2013-07-16
> **SeijiSensei said:**
> use pg_dumpall to create a plain-text backup of the database(s).
I couldn't do pg_dumpall!
```
linux-server Desktop # pg_dumpall --post=5433 --username=postgres --password --host=localhost --verbose
Error: No existing local cluster is suitable as a default target. Please see man pg_wrapper(1) how to specify one.
linux-server Desktop #
```

> Once you get everything running, you should create a script running from cron that does this at least once a day.
Why I need to create this script? I want to migrate to pg 9.2 once for all

---

### Post by SeijiSensei on 2013-07-16
> **mbnoimi said:**
> I couldn't do pg_dumpall!
```
linux-server Desktop # pg_dumpall --post=5433 --username=postgres --password --host=localhost --verbose
Error: No existing local cluster is suitable as a default target. Please see man pg_wrapper(1) how to specify one.
linux-server Desktop #
```

I believe you meant "--port".

> Why I need to create this script? I want to migrate to pg 9.2 once for all

The fact that you don't have an existing dumpfile to import to 9.2 tells me you're not making daily backups of the PostgreSQL database.  You might want to rethink your backup procedures after you finish the upgrade.  I run pg_dumpall every night and ship a copy of the file to an offsite machine as well as making a local copy.  I once lost an entire PG instance without proper backups in place; it wasn't a pretty sight.

---

### Post by mbnoimi on 2013-07-17
Thanks a lot for help. I found awesome guide at: [https://wiki.postgresql.org/wiki/Using_pg_upgrade_on_Ubuntu/Debian#Upgrading_to_version_9.2_or_later](https://wiki.postgresql.org/wiki/Using_pg_upgrade_on_Ubuntu/Debian#Upgrading_to_version_9.2_or_later)

---

