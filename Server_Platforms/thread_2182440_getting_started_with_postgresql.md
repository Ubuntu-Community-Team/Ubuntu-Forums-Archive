---
title: "getting started with postgresql"
date: 2013-10-21
forum: Server Platforms
---

### Post by Lars Noodén on 2013-10-21
Are there some good, concise tutorials or guides for learning Postgresql for those coming from MySQL?  I would want to work through the regular psql client.  I'm looking for just simple stuff like the basic connection, adding users, databases and tables.  MariaDB is not in the repository yet and MySQL's time is over, but there seems to be a shortage of material for beginners for Postgresql.

---

### Post by SeijiSensei on 2013-10-22
I've always found the documentation for PostgreSQL very comprehensible.  It starts with a [tutorial]("http://www.postgresql.org/docs/9.1/static/tutorial.html").

Some things are much easier in PostgreSQL than MySQL, particularly user account management.  One hint at the start is to learn how to become the "postgres" user that owns and administers the entire installation.  If you run the command "sudo su postgres" you will then have admin privileges.  The first thing I would do is create a user account for yourself that matches your Linux login.  So if you log in as "lars" you would do this:

```

lars$ sudo su postgres
postgres$ createuser lars
exit

```

Now you can create databases as PG user lars.  From your own command prompt, create a test database with "createdb lars".  You should be able to log into the server with "psql lars" and see your empty database.  The first thing I would do is type "help".  Use "\q" to quit the psql client.

One other hint.  Permissions are controlled by the file pg_hba.conf in the PGDATA directory.  The actual name of that directory can vary across Ubuntu versions.  It will be a branch of /var/lib like /var/lib/postgresql/data.  There are a lot of alternative permissions schemes.  I usually "trust" connections coming from known IP addresses like the VPN that connects from my desktop to my virtual server out at Linode.  The default uses "ident" on the localhost interface.  That means that only Linux user "lars" can connect to the "lars" database from the command prompt.

Any other questions, just ask.  I've used nothing by PostgreSQL for a decade now except when third-party web applications like WordPress prefer MySQL.

One other thing.  MySQL does not adhere to ISO standards as closely as PostgreSQL does.  That makes it difficult to use mysqldump to create a database backup and import it directly into PostgreSQL.  Things like the engine definitions (e.g., "InnoDB") in the MySQL CREATE TABLE command have no PG equivalents.  If you remove the MySQLisms, it's fairly easy to transfer a database.  Alternatively, I have used MS Access for tasks like this with ODBC connections to the source MySQL DB and target PostgreSQL DB.

---

### Post by Lars Noodén on 2013-10-23
I was missing that there are system utilities and a system user (postgres).  

That and the tutorial gets me started.  Thanks.

---

