---
title: "Need some help w/ setting up a server control panel"
date: 2005-11-09
forum: Server Platforms
---

### Post by _cashel on 2005-11-09
I'm trying to setup the [SCInterface]("http://games.scinterface.com/") game server control panel and am very lost. Because I am using the open source version, I basically receive no support from them. When I execute the install file for the app, it extracts a bunch of files and then gives me the following:

```
Updating the locate database, this might take a while depending on
when you last did this, and the I/O of your system
Installing scm_types.so
System Changes
Database changes
    Making sure database server is upSCManager/db/scm_setup.sh: line 222: /etc/init.d/postgresql: No such file or directory

psql: could not connect to server: No such file or directory
        Is the server running locally and accepting
        connections on Unix domain socket "/tmp/.s.PGSQL.5432"?
    Creating the database user
createuser: could not connect to database template1: could not connect to server: No such file or directory
        Is the server running locally and accepting
        connections on Unix domain socket "/tmp/.s.PGSQL.5432"?
Error creating database user.  Please look at previous errors.
Error executing the SCM database setup script.
Please look at previous errors

```

I've installed the following: postgresql, libapache2-mod-auth-pgsql, php4-pgsql, and pgadmin3. The problem is I have no clue how to use any of it. I can deal with websites and mysql, but I don't know where to begin with this. I'm trying not to be as vague as possible, but what exactly do I need to do to go from where I'm at now to getting this thing to work? I haven't done anything other than install the dependencies. It looks like I need to create a user for this to all work, how do I do that?

---

### Post by _cashel on 2005-11-09
I'm making some headway. I renamed /etc/init.d/postgresql-7.4 to /etc/init.d/postgresql, and now I'm getting an error stating that the postgresql service can't start because TCP/IP connections must be enabled for SSL. I thought I had read that to get this to work, you must create a key and certificate. I've done this, but I have no clue where I am supposed to place these two files to get it to accept tcp/ip connections.

edit: Here's the error I'm receiving now:
```
Updating the locate database, this might take a while depending on
when you last did this, and the I/O of your system
Installing scm_types.so
System Changes
Database changes
    Making sure database server is upThe PostgreSQL server failed to start. Please check the log output:
/usr/lib/postgresql/7.4/bin/postmaster: TCP/IP connections must be enabled for SSL

psql: could not connect to server: No such file or directory
        Is the server running locally and accepting
        connections on Unix domain socket "/tmp/.s.PGSQL.5432"?
    Creating the database user
createuser: could not connect to database template1: could not connect to server: No such file or directory
        Is the server running locally and accepting
        connections on Unix domain socket "/tmp/.s.PGSQL.5432"?
Error creating database user.  Please look at previous errors.
Error executing the SCM database setup script.
Please look at previous errors
```

---

### Post by _cashel on 2005-11-10
anybody?

---

