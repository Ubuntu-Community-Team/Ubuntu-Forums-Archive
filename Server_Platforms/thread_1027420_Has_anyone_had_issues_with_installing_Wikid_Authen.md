---
title: "Has anyone had issues with installing Wikid Authentication Server on Ubuntu ?"
date: 2009-01-01
forum: Server Platforms
---

### Post by sil3nt on 2009-01-01
Hi guys has anyone tried this ? I have been trying to do so by following :[http://www.wikidsystems.com/documentation/installation-documentation/How%20to%20install%20the%20WiKID%20Strong%20Authentication%20Server%20on%20Ubuntu]("http://www.wikidsystems.com/documentation/installation-documentation/How%20to%20install%20the%20WiKID%20Strong%20Authentication%20Server%20on%20Ubuntu")
but I cant get things to work I think it maybe my postgresql setup although I followed the instructions to the T.

I get this problem when I do the first boot config (as root) for Wikid and I get permission errors if I try and do it via the postgres user.. any ideas ?: ```
Initializing PostgreSQL data directories [start] ...
 * Starting PostgreSQL 8.3 database server                               [ OK ] 
Initializing PostgreSQL data directories [stop] ...
 * Stopping PostgreSQL 8.3 database server                               [ OK ] 
dropdb: could not connect to database postgres: could not connect to server: No such file or directory
	Is the server running locally and accepting
	connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?

```

I am assuming this is a user priv based issue but its doing my head in, because I cant get it working ;)

Cheers in advance (I am using Ubuntu Jeos 8.10)

---

### Post by nowen on 2010-03-31
> **sil3nt said:**
> Hi guys has anyone tried this ? I have been trying to do so by following :[http://www.wikidsystems.com/documentation/installation-documentation/How%20to%20install%20the%20WiKID%20Strong%20Authentication%20Server%20on%20Ubuntu]("http://www.wikidsystems.com/documentation/installation-documentation/How%20to%20install%20the%20WiKID%20Strong%20Authentication%20Server%20on%20Ubuntu")
but I cant get things to work I think it maybe my postgresql setup although I followed the instructions to the T.

I get this problem when I do the first boot config (as root) for Wikid and I get permission errors if I try and do it via the postgres user.. any ideas ?: ```
Initializing PostgreSQL data directories [start] ...
 * Starting PostgreSQL 8.3 database server                               [ OK ] 
Initializing PostgreSQL data directories [stop] ...
 * Stopping PostgreSQL 8.3 database server                               [ OK ] 
dropdb: could not connect to database postgres: could not connect to server: No such file or directory
	Is the server running locally and accepting
	connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?

```

I am assuming this is a user priv based issue but its doing my head in, because I cant get it working ;)

Cheers in advance (I am using Ubuntu Jeos 8.10)


Can you start postgres by itself?  

Nick

---

