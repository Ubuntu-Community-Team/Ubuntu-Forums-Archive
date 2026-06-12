---
title: "Unable to import MariaDB backup."
date: 2020-10-28
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2020-10-28
My other thread on this - [https://www.linuxquestions.org/questions/linux-server-73/mariadb-failing-to-import-backup-4175684350/](https://www.linuxquestions.org/questions/linux-server-73/mariadb-failing-to-import-backup-4175684350/)

Been moving myself into Docker lately and hit a snag on trying to do my MariaDB server.

```
$ zcat mydatabases.2020.10.28.07.21.sql.gz | docker exec -i mariadb mysql
ERROR 1556 (HY000) at line 5331: You can't use locks with log tables
read unix @->/run/docker.sock: read: connection reset by peer
```

I've narrowed this down to involving Focal some how. On an 18.04 LXD container I can import. On an 18.04 Docker container on an 18.04 host I can import. Anytime the host is 20.04 based, either bare metal or LXD this error comes up on attempted import regardless of Docker container being Bionic or Focal. It also had the same failure on my laptop which was freshly installed Focal Xubuntu recently with zero customizing or packages. Just reinstalled it and haven't touched it since.

---

### Post by LHammonds on 2020-10-29
I would imagine that your backup includes the "mysql" system database and as such, you cannot restore certain system tables while they are in use...specifically the general and slow log tables.

You need to be careful when restoring system databases and ensure you actually mean to do this.  I have only ever restored system databases whenever I was restoring to the exact same server (e.g. reverting to a point in time).  When migrating to a different / fresh server, there can be issues going to different versions of the OS, database engine or different kind of database (mysql -> mariadb).

It sounds like you are trying to migrate from Ubuntu 18.04 to 20.04 and as such, I would "NOT" include the system databases.  However, you should make sure your backup exports the data you need from the system databases such as users/roles, grants and stored procedures.  If you only export user databases, you will find that your accounts will not work on a different system if you did not explicitly export the users/grants.

You "could" just tell it to ignore locked tables but that would be foolish given what you are trying to accomplish (Ubuntu 18->20 and unspecified version of MariaDB -> unspecified version of MariaDB)

If you do not know how to export the necessary bits out of the system database, you can look through my [custom backup script]("https://github.com/LHammonds/ubuntu-bash/blob/master/db-backup.sh").  At line 244 is a function that exports users and roles (mariadb 10.x and above only....does not work for mysql).   At line 261 I export all databases except those in an exclusion list...this is where you would want to add the 3 system databases so the export only includes user databases.

The variable setting at the top of the script ensures I do not include the system databases in my "all databases" archives.
```
DatabasesToExclude="'information_schema','mysql','performance_schema','JunkUserDB1','JunkUserDB2'"
```

**EDIT**: Make sure you clarify what version of MariaDB you have at the source and target for yourself and anyone trying to help you.

LHammonds

---

### Post by Tadaen_Sylvermane on 2020-10-29
You got it. I ended up doing exactly as you suggested.  Posing same thing I posted on other forum. Thank you for pointing me in right place.

> Not solved but worked around. Dumped my personal dbs individually. Made .sql file to create my few users and grants. Started new container and imported each in turn manually creating the empty dbs as needed for import.

---

