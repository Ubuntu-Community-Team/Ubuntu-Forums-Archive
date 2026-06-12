---
title: "postfix smtp connection refused"
date: 2005-03-29
forum: Server Platforms
---

### Post by koan on 2005-03-29
Hello, I wonder if anyone can help me with this problem.

I have altered the postfix config so that it now accepts port 25 connections from my local network.  The problem I am having is that email isn't being forwarded onto where it needs to go.

In main.cf, I have "relay hosts =" to indicate that postfix should resolve the MX record and forward email directly to the recipient email server.

In the mail.log, I am getting:

Mar 28 20:33:56 localhost postfix/qmgr[3190]: warning: connect to transport smtp: Connection refused

Here is my master.cf (I put the absolute references for smtp in myself):

10.1.1.2:smtp inet n   -       -       -       -       smtpd
::1:smtp       inet n   -       -       -       -       smtpd
#submission inet n      -       -       -       -       smtpd
#       -o smtpd_etrn_restrictions=reject
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       -       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
smtp      inet  n       -       -       -       -       /usr/lib/postfix/smtp
relay     unix  n       -       -       -       -       /usr/lib/postfix/smtp
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       n       -       -       lmtp
anvil     unix  -       -       n       -       1       anvil

main.cf:

myhostname = mydomain
mydomain = home.mydomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost.home.mydomain.com, localhost
relaydomains = mydomain.biz, mydomain.com, mydomain.co.uk
relayhost =
mynetworks = 127.0.0.0/8, 10.1.1.0/24
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +

===================


Does anyone know why the smtp daemon is refusing the connection, or how I can debug it?  

Thanks,

koan

---

### Post by koan on 2005-03-29
I should point out I am using warty...

---

### Post by alastair on 2005-03-30
In "master.cf", where's the client smtp? i.e.

```

smtp      unix  -       -       -       -       -       smtp

```

---

### Post by koan on 2005-03-30
Hmm.

I had "n" in for "not private" and changed it to "-" on the smtp client line in master.cf, and now email flows.

Any ideas?

It is working though, thanks Alistair.

---

