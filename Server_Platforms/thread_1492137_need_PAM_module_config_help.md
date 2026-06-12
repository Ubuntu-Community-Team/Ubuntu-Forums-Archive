---
title: "need PAM module config help"
date: 2010-05-24
forum: Server Platforms
---

### Post by smaring on 2010-05-24
I'm trying my best to understand the PAM configuration syntax, but I'm thinking perhaps I've killed too many brain cells, because I'm just not catching on ...

I am trying to configure an "imap" and "smtp" pam module for saslauthd to authenticate to my database.

What I am experiencing is that only username/password combinations that can first authenticate against the local unix accounts (i.e. /etc/passwd /etc/shadow) are actually allowed to even attempt an auth with my mysql module.

How do I configure this so that, for these services, my mysql config is the only and final answer for these services?

here is my /etc/pam.d/imap:
```

@include common-auth
@include common-account

account optional pam_mysql.so \
   host=/var/run/mysqld/mysqld.sock \
   user=openexchange \
   passwd=idogirls \
   db=oxdatabase_6 \
   [table=login2user LEFT JOIN user ON login2user.id=user.id AND login2user.cid=user.cid] \
   [where=user.cid=1] \
   usercolumn=user.mail \
   passwdcolumn=user.userPassword \
   crypt=1 \
   verbose=1


account required pam_mysql.so \
   host=/var/run/mysqld/mysqld.sock \
   user=openexchange \
   passwd=idogirls \
   db=oxdatabase_6 \
   [table=login2user LEFT JOIN user ON login2user.id=user.id AND login2user.cid=user.cid] \
   [where=user.cid=1] \
   usercolumn=user.mail \
   passwdcolumn=user.userPassword \
   crypt=1 \
   verbose=1

```

Thanks,
Steve Maring
Tampa, FL

---

### Post by smaring on 2010-05-24
this worked ...

```

auth sufficient pam_mysql.so \
   host=/var/run/mysqld/mysqld.sock \
   user=openexchange \
   passwd=idogirls \
   db=oxdatabase_6 \
   [table=login2user LEFT JOIN user ON login2user.id=user.id AND login2user.cid=user.cid] \
   [where=user.cid=1] \
   usercolumn=user.mail \
   passwdcolumn=user.userPassword \
   crypt=1 \
   verbose=1

account required pam_mysql.so \
   host=/var/run/mysqld/mysqld.sock \
   user=openexchange \
   passwd=idogirls \
   db=oxdatabase_6 \
   [table=login2user LEFT JOIN user ON login2user.id=user.id AND login2user.cid=user.cid] \
   [where=user.cid=1] \
   usercolumn=user.mail \
   passwdcolumn=user.userPassword \
   crypt=1 \
   verbose=1

```

---

