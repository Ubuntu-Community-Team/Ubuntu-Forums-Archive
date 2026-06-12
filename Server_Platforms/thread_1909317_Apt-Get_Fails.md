---
title: "Apt-Get Fails"
date: 2012-01-15
forum: Server Platforms
---

### Post by ddanie on 2012-01-15
I'm attempting a PostgreSQL install on an 11.10 server instance using the normal syntax:

sudo apt-get install postgresql

No errors, but it fails to create the /etc/postgresql directory and all the files and subdirectories.  Makes it rather difficult to edit conf files.  Doing a "find" on the conf files returns nothing.  The same install works perfectly on a desktop 11.10 instance.

Thoughts?

PostgreSQL 8.4.9
Ubuntu 11.04

---

### Post by Paddy Landau on 2012-01-15
It may not be installing to /etc.

Open Synaptic Package Manager (if you don't have it, install [synaptic]("apt:synaptic")). Find postgresql. Right-click > Properties > Installed Files.

---

### Post by ddanie on 2012-01-15
This is a server - no gui.

Running dpkg -s postgresql:

```

Package: postgresql
Status: install ok installed
Priority: optional
Section: database
Installed-Size: 56
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: postgresql-8.4
Version: 8.4.9-0ubuntu0.11.04
Depends: postgresql-8.4
Description: object-relational SQL database (supported version)
 PostgreSQL is a fully featured object-relational database management
 system.  It supports a large part of the SQL standard and is designed
 to be extensible by users in many aspects.  Some of the features are:
 ACID transactions, foreign keys, views, sequences, subqueries,
 triggers, user-defined types and functions, outer joins, multiversion
 concurrency control.  Graphical user interfaces and bindings for many
 programming languages are available as well.
 .
 This package always depends on the currently supported PostgreSQL
 database server version.
Homepage: http://www.postgresql.org/
Original-Maintainer: Martin Pitt <mpitt@debian.org>

```

So, it's "somewhat" installing, but the many of the files aren't copying at all.  Running a find on the conf files, for example, returns null.

Since this is happening on a server install versus a desktop install, I thought there might be something unique to server that I'm missing.

---

### Post by Paddy Landau on 2012-01-15
Try this command:
```
dpkg --listfiles postgresql
```

---

### Post by ddanie on 2012-01-15
Installed directly, and used PostgreSQL 9.1 source rather than the PostgreSQL 8 package and it worked properly.  For some reason, the package wasn't expanding the files that should go in the /etc/postgresql folder (it wasn't even creating the folder).

All is well in PostgreSQL land.

---

### Post by Paddy Landau on 2012-01-16
I'm glad that managed to solve the problem.

Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

