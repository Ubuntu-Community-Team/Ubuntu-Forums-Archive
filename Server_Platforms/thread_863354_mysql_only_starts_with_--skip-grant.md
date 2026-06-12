---
title: "mysql only starts with --skip-grant"
date: 2008-07-18
forum: Server Platforms
---

### Post by viniosity on 2008-07-18
Recently mysql has been crashing on me.  There's nothing in /var/log/mysql.err or /var/log/mysql.log though there are dozens of files in /var/log/mysql (named mysql-bin.000*** - e.g. mysql-bin.000477) as well as a mysql-bin.index file.  None of them seem to give me any hints as to why mysql is crashing though.

Further strangness is that I cannot start mysql using the regular sudo /etc/init.d/mysql start command either.  It seems to fail silently (no hints in the log file)

In order to get running, I'm having to use

```

mysqld --skip-grant

```

Does anyone know where I can look to track down this problem?

---

