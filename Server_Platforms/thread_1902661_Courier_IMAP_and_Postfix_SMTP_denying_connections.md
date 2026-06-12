---
title: "Courier IMAP and Postfix SMTP denying connections"
date: 2011-12-31
forum: Server Platforms
---

### Post by croxio5 on 2011-12-31
Hi there,

Been trying to set up a mail server for my site, been following the tutorial at [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/), but now I'm trying to set up an account inside MS Outlook 2010 and it'll fail connecting via IMAP. It says it has also sent it's test message but it looks as if it's getting denied from tailing logs.

When connecting via IMAP, here's the output:
```
Dec 31 14:12:24 pandorica imapd-ssl: Connection, ip=[::ffff:81.156.224.250]
Dec 31 14:12:25 pandorica imapd-ssl: LOGIN FAILED, user=ciaran@nitranetworks.co.uk, ip=[::ffff:81.156.224.250]

```

Test message sending outputs this:
```
Dec 31 14:14:10 pandorica postfix/smtpd[30376]: connect from host81-156-224-250.range81-156.btcentralplus.com[81.156.224.250]
Dec 31 14:14:10 pandorica postfix/smtpd[30376]: NOQUEUE: reject_warning: RCPT from host81-156-224-250.range81-156.btcentralplus.com[81.156.224.250]: 504 5.5.2 <CiaranPC>: Helo command rejected: need fully-qualified hostname; from=<ciaran@nitranetworks.co.uk> to=<ciaran@nitranetworks.co.uk> proto=ESMTP helo=<CiaranPC>
Dec 31 14:14:10 pandorica postfix/smtpd[30376]: E757927386A1: client=host81-156-224-250.range81-156.btcentralplus.com[81.156.224.250]
Dec 31 14:14:11 pandorica postfix/cleanup[30379]: E757927386A1: message-id=<>
Dec 31 14:14:11 pandorica postfix/qmgr[28576]: E757927386A1: from=<ciaran@nitranetworks.co.uk>, size=630, nrcpt=1 (queue active)
Dec 31 14:14:11 pandorica postfix/virtual[30380]: E757927386A1: to=<ciaran@nitranetworks.co.uk>, relay=virtual, delay=0.88, delays=0.87/0/0/0, dsn=2.0.0, status=sent (delivered to maildir)
Dec 31 14:14:11 pandorica postfix/qmgr[28576]: E757927386A1: removed
Dec 31 14:14:11 pandorica postfix/smtpd[30376]: disconnect from host81-156-224-250.range81-156.btcentralplus.com[81.156.224.250]

```

Is there anything I'm doing wrong? Could someone please help me out?

Regards,

~***C***

---

### Post by 2F4U on 2011-12-31
Maybe different password encryption settings (assuming that the password you configured is the same for client and server)?

---

### Post by croxio5 on 2011-12-31
It's been configured the same as per the tutorial, it's just encrypt()ed via MySQL, i.e. adding a new user means doing this query:

```
INSERT INTO users ('id','name','maildir','crypt') VALUES ('user@host','user-host','user-host/',encrypt('password'))
```

---

### Post by SeijiSensei on 2012-01-02
```
Dec 31 14:14:10 pandorica postfix/smtpd[30376]: NOQUEUE: reject_warning: RCPT from host81-156-224-250.range81-156.btcentralplus.com[81.156.224.250]: 504 5.5.2 <CiaranPC>: Helo command rejected: need fully-qualified hostname; from=<ciaran@nitranetworks.co.uk> to=<ciaran@nitranetworks.co.uk> proto=ESMTP helo=<CiaranPC>
```

This might not be the only problem, but the client computer sending the message needs a "fully-qualified" hostname.  That's a name of the form host.domain.ext, like ciaranpc.example.com.  I don't use Postfix so I don't know whether you can relax this requirement.  The alternative is to name the client computer something like ciaranpc.nitranetworks.co.uk.

---

