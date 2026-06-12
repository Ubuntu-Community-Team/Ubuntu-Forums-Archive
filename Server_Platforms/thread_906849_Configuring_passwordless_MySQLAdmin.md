---
title: "Configuring passwordless MySQLAdmin"
date: 2008-08-31
forum: Server Platforms
---

### Post by mattofak on 2008-08-31
Hey all, I recently migrated my MySQL datastore from one disk to another and I accidently deleted my permissions table. This poses the problem that I dont know what ubuntu expects in order to shutdown the server. What user is it using to chroot? mysql? or another, and what other privs outside of SHUTDOWN does it require.

I quote the relevant lines from /etc/init.d/mysql
```

# * As a passwordless mysqladmin (e.g. via ~/.my.cnf) must be possible
# at least for cron, we can rely on it here, too. (although we have
# to specify it explicit as e.g. sudo environments points to the normal
# users home and not /root)

```

Thanks for any suggestions.

---

