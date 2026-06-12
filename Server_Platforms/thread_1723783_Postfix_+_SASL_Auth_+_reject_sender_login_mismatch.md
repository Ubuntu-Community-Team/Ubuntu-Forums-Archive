---
title: "Postfix + SASL Auth + reject_sender_login_mismatch"
date: 2011-04-07
forum: Server Platforms
---

### Post by mikeygstl on 2011-04-07
All,

I am attempting to tighten the reins on my mail server, as I would like to allow imap access from the outside world.  Prior to encryption, I would like to get smtpd sasl set up properly, and I am having a bit of trouble.

When attempting to implement an smtpd_sender_login_maps , allowing the use of reject_sender_login_mismatch, I have difficulty sending as anyone other that the logged in user.

For instance, logged in as [email]mike@example.com[/email], I would like to be able to send as [email]postmaster@example.com[/email].  Thus I have the following:

```

# main.cf (relevant portions)

smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sender_login_maps = mysql:/etc/postfix/virt/senders.cf
smtpd_recipient_restrictions = reject_sender_login_mismatch,permit_sasl_authenticated 
```
and 
```

# senders.cf
hosts = 127.0.0.1
user = postfixdbuser
password = somepassword
dbname = avirtualmaildb
query = SELECT address FROM postfix_valid_senders WHERE sender = '%s';
```
with the result of
```

host# postmap -q mike@example.com mysql:/etc/postfix/virt/senders.cf
mike@example.com,postmaster@example.com
```

Yet, when I attempt to send:

```

user@somehost:/etc/dovecot# telnet localhost 25
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 somehost.example.com ESMTP Postfix (Ubuntu)
ehlo x
250-somehost.example.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-AUTH PLAIN
250-AUTH=PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
AUTH PLAIN AG2RB3NotReallyMyAuthHash29jb2JlYW4=
235 2.7.0 Authentication successful
mail from: postmaster@example.com
250 2.1.0 Ok
rcpt to: mike@someother.com
553 5.7.1 <postmaster@example.com>: Sender address rejected: not owned by user mikeyg@example.com
quit
221 2.0.0 Bye
Connection closed by foreign host.
user@somehost:/etc/dovecot# 
```
and
```

Apr  7 12:08:06 somehost postfix/postfix-script[31294]: refreshing the Postfix mail system
Apr  7 12:08:06 somehost postfix/master[5593]: reload -- version 2.7.0, configuration /etc/postfix
Apr  7 12:23:36 somehost dovecot: imap-login: Login: user=<mike@example.com>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Apr  7 12:23:37 somehost postfix/smtpd[31534]: connect from localhost[127.0.0.1]
Apr  7 12:23:37 somehost postfix/smtpd[31534]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 553 5.7.1 <postmaster@example.com>: Sender address rejected: not owned by user mike@example.com; from=<postmaster@example.com> to=<mike@someother.com> proto=ESMTP helo=<example.com>
```

What am I doing wrong? :confused:

Thank you in advance for any help

---

### Post by mikeygstl on 2011-04-07
Stumbled upon my own answer.

This:
> **mikeygstl said:**
> 
```

# senders.cf
hosts = 127.0.0.1
user = postfixdbuser
password = somepassword
dbname = avirtualmaildb
query = SELECT address FROM postfix_valid_senders WHERE sender = '%s';
```


should be:

```

# senders.cf
hosts = 127.0.0.1
user = postfixdbuser
password = somepassword
dbname = avirtualmaildb
query = SELECT sender FROM postfix_valid_senders WHERE address = '%s';
```

because postfix/smtpd queries with the sending address and looks for the auth'd address within that list, not the other way around.

---

