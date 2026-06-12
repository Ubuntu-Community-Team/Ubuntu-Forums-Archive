---
title: "Postfix SMTP TLS configuration"
date: 2012-09-16
forum: Server Platforms
---

### Post by Ortix on 2012-09-16
I'm sure this has been asked a zillion times, but I have also scoured the net for a zillion hours with no luck.

Basically, I am trying to set up a mail server. The POP3 part works perfectly fine (yay!) but the SMTP is the biggest problem. I'm pretty sure that port 25 is being blocked by my ISP (haven't checked since i don't know how) because with a standard config, I would be able to receive mail but not send. Plus I don't want to use port 25 anyway since I want my outgoing mail to be encrypted.

So what did i do? I followed this tutorial (TO THE LETTER):
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

but with no luck. telnet also gives nothing. It just hangs on the first line:

```
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 icarus.ledigroup.com ESMTP Postfix (Ubuntu)

```

Then again, the only thing that I have not been able to set up is the FQDN because I want to wait before the mail is working before I can point ledigroup.com to my home server (yes home server with a single STATIC ip address, using godaddy's dns service to point all A entries to my home).

Could that be a problem or?..

Here is a tail -10 from my logfile:
```
root@Icarus:~# tail -10 /var/log/mail.log
Sep 16 13:51:04 Icarus postfix/smtp[11074]: 4BFB734026D5: to=<nicktsutsunava@gmail.com>, relay=none, delay=248561, delays=248471/0.01/90/0, dsn=4.4.1, status=deferred (connect to alt2.gmail-smtp-in.l.google.com[173.194.71.27]:25: Connection timed out)
Sep 16 14:14:34 Icarus postfix/qmgr[10655]: E9DEB34026D1: from=<info@sopoiselidze.info>, size=2664, nrcpt=1 (queue active)
Sep 16 14:15:04 Icarus postfix/smtp[11471]: connect to gmail-smtp-in.l.google.com[74.125.79.27]:25: Connection timed out
Sep 16 14:15:04 Icarus postfix/smtp[11471]: connect to gmail-smtp-in.l.google.com[2a00:1450:8005::1a]:25: Network is unreachable
Sep 16 14:15:34 Icarus postfix/smtp[11471]: connect to alt1.gmail-smtp-in.l.google.com[173.194.69.27]:25: Connection timed out
Sep 16 14:15:34 Icarus postfix/smtp[11471]: connect to alt1.gmail-smtp-in.l.google.com[2a00:1450:4008:c01::1b]:25: Network is unreachable
Sep 16 14:16:04 Icarus postfix/smtp[11471]: connect to alt2.gmail-smtp-in.l.google.com[173.194.71.27]:25: Connection timed out
Sep 16 14:16:04 Icarus postfix/smtp[11471]: E9DEB34026D1: to=<nicktsutsunava@gmail.com>, relay=none, delay=250914, delays=250824/0.01/90/0, dsn=4.4.1, status=deferred (connect to alt2.gmail-smtp-in.l.google.com[173.194.71.27]:25: Connection timed out)
Sep 16 14:19:10 Icarus postfix/smtpd[11478]: connect from localhost[127.0.0.1]
Sep 16 14:21:06 Icarus postfix/smtpd[11478]: disconnect from localhost[127.0.0.1]

```

I can't get anything usable out of this.

So in other words, how can I set up my SMTP mail server on port ?587? to be encrypted? 

Thansk so much!

---

### Post by stmiller on 2012-09-16
Port 25 is required for mail. It is how mail servers talk to other mail servers. 

You can indeed use SMTP with TLS on port 25 so that the mail server -to- mail server transaction is wrapped in TLS. However not all mail servers support this. Not many at all in fact...

I'd advise against doing mail for a business from a home ISP IP address. Cheers,

---

### Post by Ortix on 2012-09-17
> **stmiller said:**
> Port 25 is required for mail. It is how mail servers talk to other mail servers. 

You can indeed use SMTP with TLS on port 25 so that the mail server -to- mail server transaction is wrapped in TLS. However not all mail servers support this. Not many at all in fact...

I'd advise against doing mail for a business from a home ISP IP address. Cheers,

It's not business at all, it's just a home server. But it seems that my ISP is blocking port 25, how would I go about fixing that?

---

