---
title: "Postfix - SASL authentication failure"
date: 2015-06-12
forum: Server Platforms
---

### Post by salvatore5 on 2015-06-12
Hi there,
I'm a bit confused and desperated by this error log:
```
Jun 13 00:27:23 mail amavis[31724]: (31724-08) Passed CLEAN, MYNETS LOCAL [127.0.0.1] [127.0.0.1] <notifications@sav****.com> -> <sv****@hotmail.it>, Message-ID: <8a33500c0afe2b7166f7ee867183e68f@mail.sav****.com>, mail_id: DiEnNJOxFptC, Hits: -, size: 1492, queued_as: 71EC23C1439A, 225 ms
Jun 13 00:27:23 mail postfix/smtp[5008]: 415B13C14398: to=<sv****@hotmail.it>, relay=127.0.0.1[127.0.0.1]:10024, delay=0.35, delays=0.12/0/0/0.23, dsn=2.0.0, status=sent (250 2.0.0 from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 71EC23C1439A)
Jun 13 00:27:23 mail postfix/qmgr[4745]: 415B13C14398: removed
Jun 13 00:27:24 mail postfix/smtp[5032]: Untrusted TLS connection established to mx2.hotmail.com[207.46.8.167]:25: TLSv1.1 with cipher ECDHE-RSA-AES256-SHA (256/256 bits)
Jun 13 00:27:25 mail postfix/smtp[5032]: 71EC23C1439A: SASL authentication failed; server mx2.hotmail.com[207.46.8.167] said: 501 Cannot decode parameter - too long
Jun 13 00:27:26 mail postfix/smtp[5032]: Untrusted TLS connection established to mx1.hotmail.com[65.55.37.72]:25: TLSv1.1 with cipher ECDHE-RSA-AES256-SHA (256/256 bits)
Jun 13 00:27:27 mail postfix/smtp[5032]: 71EC23C1439A: SASL authentication failed; server mx1.hotmail.com[65.55.37.72] said: 501 Cannot decode parameter - too long
Jun 13 00:27:28 mail postfix/smtp[5032]: Untrusted TLS connection established to mx3.hotmail.com[65.55.37.104]:25: TLSv1.1 with cipher ECDHE-RSA-AES256-SHA (256/256 bits)
Jun 13 00:27:28 mail postfix/smtp[5032]: 71EC23C1439A: SASL authentication failed; server mx3.hotmail.com[65.55.37.104] said: 501 Cannot decode parameter - too long
Jun 13 00:27:30 mail postfix/smtp[5032]: Untrusted TLS connection established to mx4.hotmail.com[65.55.33.135]:25: TLSv1.1 with cipher ECDHE-RSA-AES256-SHA (256/256 bits)
Jun 13 00:27:30 mail postfix/smtp[5032]: 71EC23C1439A: SASL authentication failed; server mx4.hotmail.com[65.55.33.135] said: 501 Cannot decode parameter - too long
Jun 13 00:27:32 mail postfix/smtp[5032]: Untrusted TLS connection established to mx3.hotmail.com[65.55.37.72]:25: TLSv1.1 with cipher ECDHE-RSA-AES256-SHA (256/256 bits)
Jun 13 00:27:32 mail postfix/smtp[5032]: 71EC23C1439A: to=<sv****@hotmail.it>, relay=mx3.hotmail.com[65.55.37.72]:25, delay=9, delays=0.14/0.01/8.9/0, dsn=4.0.0, status=deferred (SASL authentication failed; server mx3.hotmail.com[65.55.37.72] said: 501 Cannot decode parameter - too long)

```
What's wrong?

---

### Post by starscalling on 2015-11-10
ever get this one worked out? i'm seeing something similar on a server i'm troubleshooting

---

### Post by smtp on 2015-11-17
It is look that mxX.hotmail.com does not support SASL authentication. Would you please paste /etc/postfix/main.cf here?

---

