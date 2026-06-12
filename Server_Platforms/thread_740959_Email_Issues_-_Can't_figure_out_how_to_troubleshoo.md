---
title: "Email Issues - Can't figure out how to troubleshoot them."
date: 2008-03-31
forum: Server Platforms
---

### Post by 3D Peruna on 2008-03-31
Running 6.1, updated. The server is hosting multiple domains - email and web using ISPConfig. Up until last week, everything worked just great (especially, after upgrading it to 2 Gig of RAM) and has been for at least 6-8 months.

Here's the problem:

We can send mail just fine.  POP3 and web interfaces work swell.  But we don't get email. I've checked the DNS services (not running on the machine itself, but a combination of Zoneedit, Edit DNS and Afraid).

But the machine itself isn't receiving mail.  Unless I reboot.  Then it starts getting mail again, for a while, but within about 12 hours, the mail stops coming.  Rebooting starts the mail flow again.  Also, if I send mail from one email account to another on the server (different domains), they don't come through immediately, as they used to do.  It takes some time for them to show up--and sometimes only after a reboot.  Postfix /flush doesn't make a difference.

All of the hosted web sites work fine.

Any suggestions as to what might be wrong?  It's getting a bit frustrating to figure out and track down.

---

### Post by Mr. C. on 2008-04-01
First try to debug on the mail server machine itself.

Connect to the server, entering the lines below, replacing the yourdomain.com and [email]you@yourdomain.com[/email] with the appropriate replacements.  The mail server will respond after each line you enter:

```
telnet localhost 25
EHLO yourdomain.com
MAIL FROM:<you@yourdomain.com>
RCPT TO:<root@localhost>
DATA
Subject: Hello
.
QUIT
```
btw. that is a single dot on the line before the QUIT command.

What does the postfix log messages show when you make this connection?

---

### Post by 3D Peruna on 2008-04-01
[INDENT]root@machine:/home/machine# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 *domain.com* ESMTP Postfix (Ubuntu)
EHLO domain.com
250-machine.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
RCPT TO:<root@localhost>
503 5.5.1 Error: need MAIL command
MAIL FROM:<me@domain.com>
250 2.1.0 Ok
DATA
554 5.5.1 Error: no valid recipients
Subject: Hello
221 2.7.0 Error: I can break rules, too. Goodbye.
Connection closed by foreign host.
[/INDENT]

Is what I get.  Nothing odd in the logs.

---

### Post by Mr. C. on 2008-04-01
In my haste, I had reversed the order of MAIL FROM and RCPT TO (they are corrected above). Please redo, and post logs (don't interpret for us).

---

### Post by 3D Peruna on 2008-04-01
Mail.log File:

[INDENT]Apr  1 10:56:43 mail postfix/cleanup[29788]: 453B8BF46E7: message-id=<20080401155633.453B8BF46E7@domain.com>
Apr  1 10:56:43 mail postfix/qmgr[27023]: 453B8BF46E7: from=<me@domain.com>, size=376, nrcpt=1 (queue active)
Apr  1 10:56:43 mail postfix/local[26183]: 453B8BF46E7: to=<mail@mail.domain.com>, orig_to=<root@localhost>, relay=local, delay=20, delays=20/0/0/0.18, dsn=$
Apr  1 10:56:43 mail postfix/qmgr[27023]: 453B8BF46E7: removed
[/INDENT]

---

### Post by Mr. C. on 2008-04-01
The postfix/local log line is truncated - where's the rest of the important information?

---

### Post by 3D Peruna on 2008-04-01
Missing info in bold.

> **3D Peruna said:**
> Mail.log File:

[INDENT]Apr  1 10:56:43 mail postfix/cleanup[29788]: 453B8BF46E7: message-id=<20080401155633.453B8BF46E7@domain.com>
Apr  1 10:56:43 mail postfix/qmgr[27023]: 453B8BF46E7: from=<me@domain.com>, size=376, nrcpt=1 (queue active)
**Apr  1 10:56:43 mail postfix/local[26183]: 453B8BF46E7: to=<mail@mail.domain.com>, orig_to=<root@localhost>, relay=local, delay=20, delays=20/0/0/0.18, dsn=2.0.0, status=sent (delivered to command:  procmail -a "$EXTENSION")**
Apr  1 10:56:43 mail postfix/qmgr[27023]: 453B8BF46E7: removed
[/INDENT]

---

### Post by Mr. C. on 2008-04-01
Ok, so we know that Postfix *is* receiving email, and delivering to procmail.  Was this expected to fail?

Next, you need to do the same thing from another machine on the LAN if possible, and on the WAN if possible.

Try the same test from those two different locations.  I can help if you don't have access to a WAN machine (IM me your server's IP address).

---

### Post by 3D Peruna on 2008-04-08
Strangely enough, the problem seems to have resolved itself--it was a DNS issue at the registrar.  They won't tell me exactly what went wrong, but after they rebuilt their tables, all worked as it did before.  What still has me confused was that some domains worked, the web sites continued to work, but only a few domains did the mail stop functioning.

However, your help did help me clean up my system an installation a bit.  It seems to be running great.  Thank you much!

---

### Post by kevdog on 2008-04-08
Mr. C

That was some great help :)

---

