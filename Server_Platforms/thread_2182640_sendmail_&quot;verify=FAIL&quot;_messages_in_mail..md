---
title: "sendmail &quot;verify=FAIL&quot; messages in mail.log"
date: 2013-10-21
forum: Server Platforms
---

### Post by talz13 on 2013-10-21
I have logcheck running, and sending notifications to NotifyMyAndroid on my phone.  I'm seeing the following messages come up whenever logcheck sends a message.  Any clue why this is happening?  It seemed to start after I rebooted the Ubuntu server.

```
Oct 21 21:02:04 server sendmail[23796]: STARTTLS=client, relay=[127.0.0.1], version=TLSv1/SSLv3, verify=FAIL, cipher=DHE-RSA-AES256-SHA, bits=256/256
Oct 21 21:02:05 server sm-mta[23797]: r9M124TR023797: from=<logcheck@server.home>, size=830, class=0, nrcpts=1, msgid=<201310220102.r9M124QG023796@server.home>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Oct 21 21:02:05 server sendmail[23796]: r9M124QG023796: to={destination address}+2@nmamail.net, ctladdr=logcheck (124/137), delay=00:00:01, xdelay=00:00:01, mailer=relay, pri=30527, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (r9M124TR023797 Message accepted for delivery)
Oct 21 21:02:05 server sm-mta[23799]: r9M124TR023797: to=<{destination address}+2@nmamail.net>, ctladdr=<logcheck@server.home> (124/137), delay=00:00:01, xdelay=00:00:00, mailer=esmtp, pri=120830, relay=mx1.nmamail.net. [50.116.38.92], dsn=2.0.0, stat=Sent (ok 1382403725 qp 32107)
Oct 21 22:02:04 server sendmail[28694]: r9M223bA028694: from=logcheck, size=527, class=0, nrcpts=1, msgid=<201310220202.r9M223bA028694@server.home>, relay=logcheck@localhost
Oct 21 22:02:04 server sm-mta[28695]: STARTTLS=server, relay=localhost [127.0.0.1], version=TLSv1/SSLv3, verify=NO, cipher=DHE-RSA-AES256-SHA, bits=256/256
Oct 21 22:02:04 server sendmail[28694]: STARTTLS=client, relay=[127.0.0.1], version=TLSv1/SSLv3, verify=FAIL, cipher=DHE-RSA-AES256-SHA, bits=256/256
Oct 21 22:02:04 server sm-mta[28695]: r9M224ix028695: from=<logcheck@server.home>, size=830, class=0, nrcpts=1, msgid=<201310220202.r9M223bA028694@server.home>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Oct 21 22:02:04 server sendmail[28694]: r9M223bA028694: to={destination address}+2@nmamail.net, ctladdr=logcheck (124/137), delay=00:00:01, xdelay=00:00:00, mailer=relay, pri=30527, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (r9M224ix028695 Message accepted for delivery)
Oct 21 22:02:04 server sm-mta[28697]: r9M224ix028695: to=<{destination address}+2@nmamail.net>, ctladdr=<logcheck@server.home> (124/137), delay=00:00:00, xdelay=00:00:00, mailer=esmtp, pri=120830, relay=mx1.nmamail.net. [50.116.38.92], dsn=2.0.0, stat=Sent (ok 1382407324 qp 1768)
```

---

### Post by SeijiSensei on 2013-10-22
Unless you have purchased an SSL certificate from a third-party provider, you will get this error.  It simply means that the certficate included with the server cannot be verified, since it is "self-signed" and not signed by a provider like Thawte or Verisign.  The transfer will still be encrypted, but the identity of the server cannot be verified.

---

### Post by talz13 on 2013-10-23
Thanks, I've added this to logcheck's ignore filters now.

---

