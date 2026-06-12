---
title: "MySQL problem: &quot;Incorrect key file for table ...&quot;"
date: 2010-07-28
forum: Server Platforms
---

### Post by pytheas22 on 2010-07-28
I'm trying to migrate a mysql server to new hardware.  The old server runs mysql 4.1.12 on RHEL 4; the new server is mysql 5.1.41 on Ubuntu 10.04.  I've been having some strange issues trying to migrate one of the databases.  I tried using mysqldump, but the file won't import properly into the new server because it complains about duplicate keys on a particular table, even though I've checked and am pretty sure there are in fact no duplicate keys.

Since I spent several days fighting with the mysqldump approach without finding a solution, I decided instead to copy the entire /var/lib/mysql directory from the old server to the new one.  This seemed to work well, with mysql starting up without complaining and all of the data seemingly present.  However, a Web application that uses one of the databases fails to work, complaining, "Incorrect key file for table 'activities'; try to repair it, line194" (interestingly, the table that I'm having trouble with is *not* the one that mysqldump was unable to import, although they are both on the same database).

I've run REPAIR TABLE on this table from within the mysql shell, but it fails with the output:

```
+----------------------+--------+----------+------------------------------------------------------------+
| Table                | Op     | Msg_type | Msg_text                                                   |
+----------------------+--------+----------+------------------------------------------------------------+
| databasename.activities | repair | Error    | Incorrect key file for table 'activities'; try to repair it |
| databasename.activities | repair | error    | Corrupt                                                    |
+----------------------+--------+----------+------------------------------------------------------------+
2 rows in set (0.00 sec)

```

I also tried myisamchk with the --recover and --safe-recover flags for this table.  In both cases, it says it fixed errors, but the Web application still complains about an incorrect key file.

What confuses me most is that (while mysqld is shut down) I've run an md5sum on the MYI file for the table in question, and it's identical on both the old server and the new server.  If the table files are identical on the two machines, I'm puzzled as to why the key file is incorrect on one but not the other.  I almost suspect this is a bug with mysql, but I'm not positive.

I'd be really grateful for any help or suggestions, as I'm out of ideas on how to solve this.  But I'm no mysql guru, so maybe I'm missing something obvious.  I would even upload the problematic table to anyone who wanted to take a look.

---

### Post by rubylaser on 2010-07-29
Why don't you upload the table so that we can actually look at, and maybe repair the problem for you.  Running REPAIR TABLE 'activities'; Should have fixed it for you, so I'd be interested to see if I can find the problem.

You could try to repair this way...

```
REPAIR TABLEe activities use_frm;
```

It's a more forceful way of getting it to repair it.

---

### Post by pytheas22 on 2010-07-30
Thanks for your response.  I don't want to upload the table publicly because it contains private data, although I appreciate your offer to look at it.

After more investigation, I think at least part of the issue is mysql versions.  According to the [mysql manual]("http://dev.mysql.com/doc/refman/5.1/en/upgrading.html"), you can't take databases created on 4.1 and have them work on 5.1.  Instead, you're supposed to do incremental upgrades (4.1>5.0>5.1), repairing the tables after each upgrade.

Strangely, I tried that aproach and although many errors with the databases were fixed after each upgrade, there were a few tables that just wouldn't repair, and I couldn't get useful output about what was wrong.

In the end, we decided just to downgrade to mysql 4.1 on the new server (we installed it by using the Dapper repositories).  Since the Web application that uses the database whose tables were causing all the problems was written in-house and has no documentation, we're not even sure it would work properly with mysql 5.1, so it seems safer to stick with an older version until someone can sit down and look at the php to figure out what exactly is going on.  Under 4.1, mysqlcheck says all the databases are clean, whether we import them with a dump file or by rsyncing over the data files manually.

If I figure out anything else about this I'll post back.  Thanks again for your help--I appreciate the response and the tip about the use_frm option (for what it's worth, I think I ran mysqlcheck --repair yesterday with an option that is equivalent to use_frm in the mysql shell, according to the manual and it still didn't work).

---

