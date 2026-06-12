---
title: "Configure POSTFIX"
date: 2012-07-04
forum: Server Platforms
---

### Post by Tres_Iqus on 2012-07-04
I need config postfix to sends mail to hotmail. now I can not send emails

please help =)


Best regards

---

### Post by lisati on 2012-07-04
*Thread moved to **Server Platforms**.*

Do you have any error messages from postfix's logs that you can share? The relevant logs can be found usually be found in /var/log/mail.log

(Remember to obscure personal information e.g. email addresses)

---

### Post by Tres_Iqus on 2012-07-04
Jul  4 17:05:23 mail amavis[22830]: (22830-13) Passed CLEAN, LOCAL [192.168.24.1] [192.168.24.1] <XXXXXXX@XXX.XX> -> <xxxxx@hotmail.com>, Message-ID: <4FF4B037.5040303@XXX.XX>, mail_id: 5gyG-ChBrAtb, Hits: -2.91, size: 861, queued_as: 6A9C21C014A, 3287 ms
Jul  4 17:05:23 mail postfix/smtp[23995]: 2788D1BFCEF: to=<xxxxx@hotmail.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=3.4, delays=0.08/0/0/3.3, dsn=2.0.0, status=sent (250 2.0.0 Ok, id=22830-13, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 6A9C21C014A)
Jul  4 17:05:23 mail postfix/qmgr[22315]: 2788D1BFCEF: removed
Jul  4 17:05:23 mail postfix/smtp[24001]: connect to mx3.hotmail.com[65.54.188.72]:25: Connection refused
Jul  4 17:05:25 mail postfix/smtp[24001]: 6A9C21C014A: to=<xxxxx@hotmail.com>, relay=mx2.hotmail.com[65.55.37.72]:25, delay=2.3, delays=0.08/0/0.78/1.4, dsn=2.0.0, status=sent (250  <4FF4B037.5040303@XXX.XX> Queued mail for delivery)
Jul  4 17:05:25 mail postfix/qmgr[22315]: 6A9C21C014A: removed

---

### Post by stmiller on 2012-07-07
```
Jul 4 17:05:23 mail postfix/smtp[24001]: connect to mx3.hotmail.com[65.54.188.72]:25: Connection refused
```

hotmail may have strict DNS requirements to avoid spam. Does your server have valid DNS records, including PTR?

---

### Post by SeijiSensei on 2012-07-07
Can you send mail to other remote domains, just not Hotmail, or can you not send mail to any remote servers?  If the latter, your ISP has probably blocked outbound SMTP traffic from client machines on its network as an anti-spamming measure.

Try running this test:

```
telnet aspmx.l.google.com 25
```

If you cannot connect to Google's mail server as well, chances are good you are blocked.

---

