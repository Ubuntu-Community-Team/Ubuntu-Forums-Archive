---
title: "cleaning up postgresql upgrades, switching to Mysql?"
date: 2017-07-07
forum: Server Platforms
---

### Post by Heeter on 2017-07-07
Hi All,

I am slowly bringing back to life an old 12.04 Ubuntu LAPP server. I have slowly managed to upgrade to the latest 16.04.2LTS, but in the process, ended up with three postgresql installations (9.1, 9.3,9.5)

I am not at all familiar with postgresql and would like to figure out how to remove the other older installations and just leave the current and make sure that it is the one running the python/django applications working.

Also, can I switch to Mysql from here? I am way more comfortable with mysql.

Regards

---

### Post by SeijiSensei on 2017-07-08
I just installed 16.04.2 Server to a virtual machine.  It runs PostgreSQL 9.5 by default. You should remove the other two versions with apt:
```

sudo apt purge postgresql-9.1
sudo apt purge postgresql-9.3

```

I have the opposite problem from you.  I've used PG for two decades and find MySQL a pain to work with when it comes to managing users.  Administering a PostgreSQL server is much easier with handy command-line tools like createuser and createdb.  The default in PostgreSQL is that each system user can become a PG user.
```

[yourname@system ~] $ sudo -u postgres createuser yourname
[yourname@system ~] $ createdb

```
Now "yourname" is a PG user with a database named, by default, "yourname".  You can access that database from the command line when logged in as yourname with "psql".  Users can also own multiple other databases, of course.

There are a variety of command-line switches for the createuser command; type "man createuser" at a prompt for the details.

It's going to take some effort to migrate, but it's possible.  First, create a complete textual "dump" of all the PostgreSQL databases on the machine with:
```

sudo -u postgres pg_dumpall > /path/to/some/file.dump

```
That file will contain all the commands and data required to rebuild the databases in the PostgreSQL dialect.  You would need to trim most of the Postgres-only content but keep things like CREATE TABLE, CREATE INDEX, and CREATE VIEW.  You will then need to rewrite the remaining commands to conform to MySQL syntax.  I don't know how MySQL represents foreign key references, triggers, and that kind of stuff.  If you have them, you'll need to write the correct MySQL code for those, too.  PG delimits the beginning of a data block with
```
COPY tablename ( fieldlist) FROM stdin;
```
which may not be portable to MySQL. This command is then followed by the data in tab-delimited format terminated by "\." on a line by itself.  

You could also extract just the data to a spreadsheet like LibreOffice calc, add field names to the top row, and save it as a .csv file.  I'd use Microsoft Access and the MySQL ODBC connector at that point to upload the data, but you can also use the "Base" application in LibreOffice.  If you created a parallel empty database in MySQL, you could use something like Access or Base to connect to both of them and migrate tables and whatnot through the client.

---

### Post by Heeter on 2017-07-10
good morning, Thank you for your input

I uninstalled the 2 older versions of PG (PG9.1,PG9.3), so now only 9.5 is left

I am getting this error:

```

 Is the server running locally and accepting
        connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?

```

```

rach@ubuntuqc:$ pg_config --version
PostgreSQL 9.1.18
rach@ubuntuqc:$ psql --version
psql (PostgreSQL) 9.5.7

```

Regards


UPDATE: I just did a purge and reinstall of postgresql, fixed the errors, now I gotta deal with other stuff that broke during updating, like django/python

---

