---
title: "Postfix &amp; Postgresql"
date: 2007-01-05
forum: Server Platforms
---

### Post by rth on 2007-01-05
I'm trying to get Postfix and Postgresql to work on my 32-bit Edgy Server machine. I have checked out the following two guides that are particular to Ubuntu, Postfix, and Postgresql:
[http://www.codepoets.co.uk/docs/postfix_postgresql_postfixadmin_courier_howto](http://www.codepoets.co.uk/docs/postfix_postgresql_postfixadmin_courier_howto)
[http://www.lxtreme.nl/index.pl/docs/linux/dovecot_postfix_pam](http://www.lxtreme.nl/index.pl/docs/linux/dovecot_postfix_pam)

I have also reviewed the much more popular MySQL way of doing it. For some reason, I receive the following two errors (plus more, but they seem to be because of these):

```
postfix/trivial-rewrite[9370]: warning: connect to pgsql server localhost: SSL SYSCALL error: No such file or directory?

postfix/trivial-rewrite[9370]: fatal: pgsql:/etc/postfix/pgsql/virtual_alias_maps.cf(0,lock|fold_fix): table lookup problem
```

As near as I can tell, it looks like Postfix is trying to connect via SSL. I have read about changing my pg_hba.conf for Postgres to accept "hostssl", but that didn't help. The queries themselves, as well as the user/pass combos are all correct and working. ](*,) 

My final goal is to have a mail server with DB and TLS and AV/AS running on this dedicated box.

---

### Post by TheCaptain2000 on 2007-02-23
Hi, I had the same problem, I got over it by doing two things (I am not sure which one of the two solved it, maybe both)

1) I enabled postgres ssl connections by editing pg_hba.conf and adding a line 
hostssl    all   all  192.168.2.2/10   md5 
where 192.168.2.2/10 is the ip range I wanted to enable

2) I edited /etc/postfix/master.cf and disabled all chrooted services, as it comes by default all services seem to run chrooted

this should let the SSL error go...but that was not enough
then you have to go to edit the file /etc/authdeamonrc
and add a line 
authmodulelist="authpgsql"

and last but no least you have to go end edit 
/etc/courier/authpgsqlrc
anf look for the label
PGSQL_MAILDIR_FIELD

with me that label was not starting at the beginning of the line but had a trailing blank. delete it and now it should work..... atleast the pop. I haven't got the imap in order yet

Take Care
Renato

---

