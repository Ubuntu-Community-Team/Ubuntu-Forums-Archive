---
title: "Problem sending internal mail with Postfix"
date: 2010-12-18
forum: Server Platforms
---

### Post by tarahmarie on 2010-12-18
Hi, all:

I am trying to configure my internal mail server so I can send out notification emails from MediaWiki. I have Postfix working up to a point, but am getting this error when I try to send a test email.

```

tarahmarie@Tarah:/home$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 Tarah ESMTP Sendmail 8.14.3/8.14.3/Debian-9.2ubuntu1; Sat, 18 Dec 2010 08:13:12 GMT; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]
ehlo localhost
250-Tarah Hello localhost [127.0.0.1], pleased to meet you
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-EXPN
250-VERB
250-8BITMIME
250-SIZE
250-DSN
250-ETRN
250-AUTH DIGEST-MD5 CRAM-MD5
250-DELIVERBY
250 HELP
mail from: root@localhost
250 2.1.0 root@localhost... Sender ok
rcpt to: mailmaster@localhost
250 2.1.5 mailmaster@localhost... Recipient ok
data
354 Enter mail, end with "." on a line by itself
Subject: My first mail with Postfix

Hi, 
Blah.
.
421 4.3.0 collect: Cannot write ./dfoBI8DCfq006803 (bfcommit, uid=0, gid=111): No such file or directory
Connection closed by foreign host.
tarahmarie@Tarah:/home$ 


```

I've googled til my eyes are bleeding, and I'm too much of a noob to know what will and won't work without mucking things up. This is the first time I've tried to configure a mail server on my first VS; it's Meerkat.

Anyone? Thanks!

---

