---
title: "saslauthd + pam + mysql = auth fail"
date: 2010-05-21
forum: Server Platforms
---

### Post by smaring on 2010-05-21
I've upgraded to 10.04 and have been trying to configure Cyrus and Postfix to authenticate via saslauthd using libpam-mysql against my Open Xchange database.

when I ...
```

testsaslauthd -u [email]smaring@rhythix.com[/email] -p xxxxxxx -f /var/spool/postfix/var/run/saslauthd/mux -s imap
0: NO "authentication failed"

```

and I see this in my /var/log/auth.log:
```

May 21 11:32:17 server saslauthd[1999]: pam_unix(imap:auth): check pass; user unknown
May 21 11:32:17 server saslauthd[1999]: pam_unix(imap:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost= 
May 21 11:32:19 server saslauthd[1999]: DEBUG: auth_pam: pam_authenticate failed: Authentication failure
May 21 11:32:19 server saslauthd[1999]: do_auth         : auth failure: [user=smaring@rhythix.com] [service=imap] [realm=] [mech=pam] [reason=PAM auth error]

```

I have full logging enabled (I think) for mysql with this in my /etc/mysql/my.cnf:
```

log        = /var/log/mysql/mysql.log

```

but I never see the query made in the log

my /etc/default/saslauthd has:
```

START=yes
MECHANISMS="pam"
OPTIONS="-c -m /var/spool/postfix/var/run/saslauthd"
PWDIR="/var/spool/postfix/var/run/saslauthd"
PARAMS="-m ${PWDIR}"
PIDFILE="${PWDIR}/saslauthd.pid"
...

```

my /etc/pam.d/imap:
```

@include common-auth
@include common-account

auth optional pam_mysql.so \
   host=/var/run/mysqld/mysqld.sock \
   user=openexchange \
   passwd=xxxxxxxx \
   db=oxdatabase_6 \
   [table=login2user LEFT JOIN user ON login2user.id=user.id AND login2user.cid=user.cid] \
   [where=user.cid=1] \
   usercolumn=login2user.uid \
   passwdcolumn=user.userPassword \
   crypt=1 \
   log=1

account required pam_mysql.so \
   host=/var/run/mysqld/mysqld.sock \
   user=openexchange \
   passwd=xxxxxxxxx \
   db=oxdatabase_6 \
   [table=login2user LEFT JOIN user ON login2user.id=user.id AND login2user.cid=user.cid] \
   [where=user.cid=1] \
   usercolumn=login2user.uid \
   passwdcolumn=user.userPassword \
   crypt=1 \
   log=1

```

some sql to confirm things ...
```

# mysql -u openexchange -p oxdatabase_6
Enter password: 
...
mysql> select login2user.uid,user.mail,user.userPassword,user.passwordMech from login2user left join user on login2user.id=user.id and login2user.cid=user.cid where login2user.uid like 'smaring%';
+---------+---------------------+---------------+--------------+
| uid     | mail                | userPassword  | passwordMech |
+---------+---------------------+---------------+--------------+
| smaring | [email]smaring@rhythix.com[/email] | xxxxxxxxxxxxx | {CRYPT}      |
+---------+---------------------+---------------+--------------+
1 row in set (0.00 sec)

```

I can do this ...
```

# testsaslauthd -u smaring -p xxxxxxx -f /var/spool/postfix/var/run/saslauthd/mux -s imap
0: OK "Success."

```
odd thing is ... I changed the password for the system user by the same name to something else, I used the command with the password in the db, it was successful, and I didn't see any sql in the mysql logs for the query!

but ... trying to change my /etc/pam.d/imap to ...
```

@include common-auth
@include common-account

auth optional pam_mysql.so \
   host=/var/run/mysqld/mysqld.sock \
   user=openexchange \
   passwd=xxxxxxx \
   db=oxdatabase_6 \
   [table=login2user LEFT JOIN user ON login2user.id=user.id AND login2user.cid=user.cid] \
   [where=user.cid=1] \
   usercolumn=user.mail \
   passwdcolumn=user.userPassword \
   crypt=1 \
   log=1

account required pam_mysql.so \
   host=/var/run/mysqld/mysqld.sock \
   user=openexchange \
   passwd=xxxxxxxx \
   db=oxdatabase_6 \
   [table=login2user LEFT JOIN user ON login2user.id=user.id AND login2user.cid=user.cid] \
   [where=user.cid=1] \
   usercolumn=user.mail \
   passwdcolumn=user.userPassword \
   crypt=1 \
   log=1

```

didn't seem to help matters

---

### Post by smaring on 2010-05-21
I'm finally seeing some of my queries getting thru to mysql, following a reboot of the server

When I do this ...
```

# testsaslauthd -u smaring -p xxxxxxxx -f /var/spool/postfix/var/run/saslauthd/mux -s imap0: NO "authentication failed"

```

I see this in the mysql log:
```

92 Connect	openexchange@localhost on oxdatabase_6
92 Init DB	oxdatabase_6
92 Query	SELECT 0, user.userPassword FROM login2user LEFT JOIN user ON login2user.id=user.id AND login2user.cid=user.cid WHERE user.mail = 'smaring' AND (user.cid=1)
92 Quit

```

but when I add special characters to the username (e.g. use an email address for the username), the query never makes it to mysql
```

# testsaslauthd -u smaring@rhythix.com -p xxxxxxxxx -f /var/spool/postfix/var/run/saslauthd/mux -s imap
0: NO "authentication failed"

```

Is there something that I need to do to saslauthd to allow the usage of email addresses as usernames?

---

### Post by smaring on 2010-05-22
I've tried enabling realm support in saslauthd and turned of caching.

My /etc/default/saslauthd now looks like this:
```

START=yes
OPTIONS="-m /var/spool/postfix/var/run/saslauthd -r"
PWDIR="/var/spool/postfix/var/run/saslauthd"
PARAMS="-m ${PWDIR}"
PIDFILE="${PWDIR}/saslauthd.pid"

```

and I tried to do my test like this:
```

# testsaslauthd -u smaring -r rhythix.com -p xxxxxxx -f /var/spool/postfix/var/run/saslauthd/mux -s imap
0: NO "authentication failed"

```

but I don't see the query come through ... if I remove the "-r rhythix.com" option I DO see the query

the story also gets a bit curious if I try to step up one level and authenticate from IMAP:
```

# imtest -m smaring@rhythix.com -p imap localhost
S: * OK server Cyrus IMAP4 v2.2.13-Debian-2.2.13-19 server ready
C: C01 CAPABILITY
S: * CAPABILITY IMAP4 IMAP4rev1 ACL QUOTA LITERAL+ NAMESPACE UIDPLUS ID NO_ATOMIC_RENAME UNSELECT CHILDREN MULTIAPPEND BINARY SORT THREAD=ORDEREDSUBJECT THREAD=REFERENCES ANNOTATEMORE IDLE
S: C01 OK Completed
Authentication failed. no mechanism available
Security strength factor: 0

```

I have modified my /etc/imapd.conf with:
```

unixhierarchysep: yes
sasl_mech_list: PLAIN LOGIN
sasl_pwcheck_method: saslauthd
virtualdomains: yes

```

not sure why it is saying "no mechanism available"

---

