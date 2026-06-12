---
title: "pure-ftp logging options"
date: 2010-09-30
forum: Server Platforms
---

### Post by xkaliburx on 2010-09-30
PureFTP getting to work with postgres, after playing around enough, I finally got verbose logging on.  The config folder does have the following;

PGSQLConfigFile 
/etc/pure-ftpd/db/postgresql.conf

That file is setup with the correct user/port, etc. but when I connect, it seems it's using KERBEROUS_V4, I don't see it saying use Pgsql.  Am I missing another flag somewhere?  Debug below'

ep 30 11:34:39 cfs4 pure-ftpd: (?@192.168.2.54) [INFO] New connection from 192.168.2.54
Sep 30 11:34:39 cfs4 pure-ftpd: (?@192.168.2.54) [DEBUG] Command [auth] [GSSAPI]
Sep 30 11:34:39 cfs4 pure-ftpd: (?@192.168.2.54) [DEBUG] Command [auth] [KERBEROS_V4]
Sep 30 11:34:41 cfs4 pure-ftpd: (?@192.168.2.54) [DEBUG] Command [user] [tester]
Sep 30 11:34:42 cfs4 pure-ftpd: (?@192.168.2.54) [DEBUG] Command [pass] [<*>]
Sep 30 11:34:47 cfs4 pure-ftpd: (?@192.168.2.54) [WARNING] Authentication failed for user [test]
Sep 30 11:34:47 cfs4 pure-ftpd: (?@192.168.2.54) [DEBUG] Command [syst] []


I really need to see both why the above, but more important, see if the postgres connect attempt is working, the query as well as the error (if any)....

---

