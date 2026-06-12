---
title: "Postgres authentication failure"
date: 2007-11-12
forum: Server Platforms
---

### Post by Tim.R on 2007-11-12
I'm having trouble with getting postgres to authenticate users with password.  See the following:

```

# aptitude install postgresql-8.2
# su - postgres
$ createuser -s -P username
$ createdb username
$ psql -U username -d username
psql: FATAL: Ident authentication failed for user "username"
$ psql -U username
psql: FATAL: Ident authentication failed for user "username"
$ psql -U username -d username -W
Password for user username:
psql: FATAL: Ident authentication failed for user "username"
$ exit
# su - username
$ psql
Welcome to psql 8.2.5 [doesn't ask for password]
$ psql -U username
Welcome to psql 8.2.5 [doesn't ask for password]
$ psql -U username -W
Password for user username:
psql: FATAL: Ident authentication failed for user "username"

```

In summary, the problem is that I can only run psql from the user I am logged in as, and password authentication seems to be ignored.  This is no good if I am running a web server that runs as www-data and need a user's database.

I have also tried ```
alter user username with password 'password';
``` but that doesn't solve the problem.

Do I have some fundamental misunderstanding of postgres (my experience is with MySQL), or have I just missed something? 

I am running ubuntu-server 7.04

---

### Post by Tim.R on 2007-11-12
I managed to find the solution.

For those interested:
modify /etc/postgres/8.2/main/pg_hba.conf and change:
```

localhost   all   all   ident sameuser

```
to
```

localhost   all   all   md5

```

---

### Post by mirceade on 2008-05-10
Thanks dude. You've saved my day. :popcorn:

---

### Post by slowtrain on 2008-06-25
Saved my day too!  Thanks! :)

---

### Post by cuz on 2008-06-26
Mine, too! Thanks.

---

