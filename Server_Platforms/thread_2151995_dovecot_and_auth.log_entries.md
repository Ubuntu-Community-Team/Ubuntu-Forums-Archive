---
title: "dovecot and auth.log entries"
date: 2013-06-06
forum: Server Platforms
---

### Post by Nevstah on 2013-06-06
HI all

I have installed postfix, dovecot and mysql and seemingly configured everything correectly to facilitate virtual users and domains based on a mysql database.

incoming and outgoing mail works perfectly, no problems there. Dovecot is configured for POP3, the virtual users can log in and send/receive mail - nonexistant users cannot (as you would expect).

However, all is not well. for every POP3 connection, there is a dovecot entry in mail.log stating authentication failure.

I'm stuck, I really can't see where i've messed up! any ideas?

example;

>telnet localhost 110
+OK Dovecot ready.
user [email]test@domain.com[/email]
+OK
pass test
+OK Logged in.

auth.log extract;

```
Jun  6 16:26:32 postfix auth: pam_unix(dovecot:auth): check pass; user unknown
Jun  6 16:26:32 postfix auth: pam_unix(dovecot:auth): authentication failure; logname= uid=0 euid=0 tty=dovecot ruser=test@domain.com rhost=10.1.12.19
``` 

mail.log extract;

```
Jun  6 16:26:32 postfix dovecot: auth-worker: mysql(localhost): Connected to database postfix
Jun  6 16:26:32 postfix dovecot: auth-worker: Debug: pam(test@domain.com,10.1.12.19): lookup service=dovecot
Jun  6 16:26:32 postfix dovecot: auth-worker: Debug: pam(test@domain.com,10.1.12.19): #1/1 style=1 msg=Password: 
Jun  6 16:26:35 postfix dovecot: auth-worker: pam(test@domain.com,10.1.12.19): pam_authenticate() failed: Authentication failure (password mismatch?) (given password: test)
Jun  6 16:26:35 postfix dovecot: auth-worker: Debug: sql(test@domain.com,10.1.12.19): query: SELECT password, 5000 as userdb_uid, 5000 as userdb_gid FROM users WHERE email = 'test@domain.com'
Jun  6 16:26:35 postfix dovecot: auth: Debug: client out: OK#0111#011user=test@domain.com
Jun  6 16:26:35 postfix dovecot: auth: Debug: master in: REQUEST#0114019585025#01117235#0111#0116c8f348e2b4f1396d56c35522a53d66f
Jun  6 16:26:35 postfix dovecot: auth: Debug: passwd(test@domain.com,10.1.12.19): lookup
Jun  6 16:26:35 postfix dovecot: auth: passwd(test@domain.com,10.1.12.19): unknown user
Jun  6 16:26:35 postfix dovecot: auth-worker: Debug: sql(test@domain.com,10.1.12.19): SELECT '/var/mail/domain.com/test' as home, 5000 AS uid, 5000 AS gid FROM users WHERE email = 'test@domain.com'
Jun  6 16:26:35 postfix dovecot: auth: Debug: master out: USER#0114019585025#011test@domain.com#011home=/var/mail/domain.com/test#011uid=5000#011gid=5000
Jun  6 16:26:35 postfix dovecot: pop3-login: Login: user=<test@domain.com>, method=PLAIN, rip=10.1.12.19, lip=10.1.2.115, mpid=17308
Jun  6 16:27:00 postfix dovecot: pop3(test@domain.com): Connection closed top=0/0, retr=0/0, del=0/7, size=18271

```

---

### Post by SeijiSensei on 2013-06-06
You haven't told us what authentication method is being used.  The mail.log extract shows an attempt to authenticate against a MySQL database.  Is that what you are using, or are you authenticating against /etc/passwd?  Unless you have a lot of users, I'd choose the latter for simplicity.

---

### Post by CharlesA on 2013-06-06
> **SeijiSensei said:**
> You haven't told us what authentication method is being used.  The mail.log extract shows an attempt to authenticate against a MySQL database.  Is that what you are using, or are you authenticating against /etc/passwd?  Unless you have a lot of users, I'd choose the latter for simplicity.

I run dovecot on my VPS with flatfiles for users and stuff.. I see similar things in my logs, but so far I've chosen to ignore them.

---

### Post by Nevstah on 2013-06-20
> **SeijiSensei said:**
> You haven't told us what authentication method is being used.  The mail.log extract shows an attempt to authenticate against a MySQL database.  Is that what you are using, or are you authenticating against /etc/passwd?  Unless you have a lot of users, I'd choose the latter for simplicity.

sorry for the slow reply, been away

yes, i'm using MySQL as there are hundreds of users and even more aliases involved

cheers

---

### Post by SeijiSensei on 2013-06-20
Then you won't see entries in /var/log/auth.log, I believe, since the operating system is not handling the authorization.

---

### Post by Nevstah on 2013-06-20
ok, since i am seeing entries in the auth.log i must have something mis-configured somewhere, so its checking MySQL and also the OS? is that even possible?

---

