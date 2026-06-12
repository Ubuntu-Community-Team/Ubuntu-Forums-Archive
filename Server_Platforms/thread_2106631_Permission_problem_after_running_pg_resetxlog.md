---
title: "Permission problem after running pg_resetxlog"
date: 2013-01-19
forum: Server Platforms
---

### Post by fullmoonguru on 2013-01-19
Can't start Postgres after running                       pg_resetxlog.  Had to change permissions to run it.  Changed permissions back but now I get this error:

```
Expected to find it in the directory "/var/lib/postgresql/9.1/main",
but could not open file "/var/lib/postgresql/9.1/main/global/pg_control": Permission denied
```This  is in a VM and the permissions for each folder are the same as an older  snapshot in which pg is running without a problem.  Any ideas?

Nevermind.  Needed to get going so I purged & reinstalled.  I'll have to re-enter a few days of data.

---

