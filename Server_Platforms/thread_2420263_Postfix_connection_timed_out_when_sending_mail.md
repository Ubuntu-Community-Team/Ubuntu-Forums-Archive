---
title: "Postfix connection timed out when sending mail"
date: 2019-06-02
forum: Server Platforms
---

### Post by lister171254 on 2019-06-02
Running latest LTS server on two different machine/domains. One can send emails, the other fails with a connection timeout when trying to connect to the recipients server

The two server look pretty much identical as far as the mail config is concerned.
A traceroute on port 80 to gmail-smtp-in.l.google.com, while the same on port 25 fails.
I'm sure it's something obvious (not the FW), but am really stumped

Thanks

---

### Post by lister171254 on 2019-06-02
One thing I just noticed is that the relay field is populated on the server the mail works from

```
Jun  2 08:59:09 mail1 postfix/submission/smtpd[4598]: disconnect from unknown[210.185.104.16] ehlo=2 starttls=1 auth=1 mail=1 rcpt=1 data=1 quit=1 commands=8
Jun  2 08:59:09 mail1 postfix/smtp[4604]: 44B8429ED63: to=<David.beerbelly@gmail.com>, relay=gmail-smtp-in.l.google.com[66.102.1.26]:25, delay=2.4, delays=1.5/0.03/0.41/0.45, dsn=2.0.0, status=sent (250 2.0.0 OK  1559458749 j1si8222206wrq.260 - gsmtp)
Jun  2 08:59:09 mail1 postfix/qmgr[1668]: 44B8429ED63: removed

```

while this is empty for the server the emails fail to be delivered

```
Jun  2 12:03:30 mail postfix/smtp[2447]: connect to mail1.no-ip.com[8.23.224.50]:25: Connection timed out
Jun  2 12:04:00 mail postfix/smtp[2447]: connect to mail2.no-ip.com[69.65.5.119]:25: Connection timed out
Jun  2 12:04:00 mail postfix/smtp[2447]: 2EA925FA8D: to=<leo@zudiewiener.com>, relay=none, delay=3667, delays=3577/0.05/90/0, dsn=4.4.1, status=deferred (connect to mail2.no-ip.com[69.65.5.119]:25: Connection timed out)
Jun  2 12:04:00 mail postfix/qmgr[2438]: 2EA925FA8D: from=<llist@dragonclaw.net>, status=expired, returned to sender

```

Given that both master.cf and main.cf look similar I don't know why one works and the other doesn't

---

### Post by lister171254 on 2019-06-02
Looka like a DNS issue. I'm running unbound on both servers and configs look the same

---

### Post by lister171254 on 2019-06-02
DNS seems to work as it identifies and translate the mail server correctly, so back to square 1

---

### Post by lister171254 on 2019-06-04
Turns out my ISP blocked port 25

---

