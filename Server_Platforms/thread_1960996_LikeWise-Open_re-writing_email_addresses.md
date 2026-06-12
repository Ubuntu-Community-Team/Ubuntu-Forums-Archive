---
title: "LikeWise-Open re-writing email addresses?"
date: 2012-04-18
forum: Server Platforms
---

### Post by VanJr on 2012-04-18
Server: Ubuntu 11.10 x64
LikeWise-Open: 6.1.0.406

**Problem**:
Email sent from the server is being relayed by a smarthost but the email address is being re-written. 

```

# sendmail -tv
To: myname@valid-domain.com
Subject: test

This is a test message. ^D
myname@valid-domain.com... Connecting to [127.0.0.1] via relay...
220 lwt1.valid-domain.com ESMTP Sendmail 8.14.4/8.14.4/Debian-2ubuntu2; Wed, 18 Apr 2012 10:36:51 -0400; (No UCE/UBE) logging access from: lwt1.valid-domain.com(OK)-lwt1.valid-domain.com [127.0.0.1]
>>> EHLO lwt1.valid-domain.com
250-lwt1.valid-domain.com Hello lwt1.valid-domain.com [127.0.0.1], pleased to meet you
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-EXPN
250-VERB
250-8BITMIME
250-SIZE
250-DSN
250-ETRN
250-AUTH GSSAPI DIGEST-MD5 CRAM-MD5
250-DELIVERBY
250 HELP
>>> VERB
250 2.0.0 Verbose mode
>>> MAIL From:<myname@lwt1.valid-domain.com> SIZE=50 AUTH=myname@lwt1.valid-domain.com
250 2.1.0 <myname@lwt1.valid-domain.com>... Sender ok
>>> RCPT To:<myname@dc1.valid-domain.com>
>>> DATA
250 2.1.5 <myname@dc1.valid-domain.com>... Recipient ok
354 Enter mail, end with "." on a line by itself
>>> .
050 <myname@dc1.valid-domain.com>... Connecting to mail.valid-domain.com. via relay...
050 220 mail.valid-domain.com

```Note that my email address was re-formed to be **myname@dc1.valid-domain.com .** 
dc1.valid-domain.com is our Microsoft Active Directory / Domain Controller. 

An identical test box that does **not** have LikeWise-Open installed does send email just fine.

Where do I fix this rule re-write?
I can't seem to find it in the sendmail configuration.

---

### Post by VanJr on 2012-04-18
Found it. Wasn't a LikeWise-Open problem. 

The problem was in the /etc/hosts file:

This */etc/hosts* entry does **NOT** play nice:
```

10.1.2.3 dc1.valid-domain.com valid-domain.com

```This */etc/hosts* entry does play nice:
```

10.1.2.3 valid-domain.com dc1.valid-domain.com

```

---

