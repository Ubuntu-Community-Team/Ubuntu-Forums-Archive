---
title: "Unable to login to postgres database"
date: 2009-10-19
forum: Server Platforms
---

### Post by Z.K. on 2009-10-19
I just installed the postgres database and it will not accept any password.  How do I set up a user and password for it.  I followed a couple of howtos, but they did not help.  

Can someone tell me how to fix this thing so I can log into it.  I am very new at this so I am not sure what to do with the config files.

I have tried changing the password, but still I cannot login to the postgres database using user postgres. 

prompt$su - postgres
Password: 
su: Authentication failure

or 

phpPgAdmin:
Login disallowed for security reasons.

How do I add a new user and password?

:confused:

---

### Post by rjs1064 on 2010-01-12
i am having the same problem, trying to get sql-ledger to work.

---

### Post by James79 on 2010-01-14
By default, the postgres user of the database will have no password set. Simply impersonating the postgres user via sudo is enough to get you into the db:

```
$ sudo -u postgres psql postgres
```

If you get prompted for a password, enter in your normal sudo admin password.

You should then be at the postgres prompt. If you want to give the postgres user a password (instead of leaving it blank), do:

```
postgres=# \password
```

in the psql tool's prompt.

---

