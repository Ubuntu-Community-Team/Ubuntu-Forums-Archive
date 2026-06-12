---
title: "Configuration issue with Sendmail TLS on Ubuntu"
date: 2013-06-21
forum: Server Platforms
---

### Post by Riunixteam on 2013-06-21
Hi, 

We have sendmail running on a virtual Ubuntu server which is acting as a relay server. We are trying to configure TLS encryption on sendmail. 
We have configured using the following link: [http://weldon.whipple.org/sendmail/starttlstut.html](http://weldon.whipple.org/sendmail/starttlstut.html)

After configuration, we can see the below status in telnet: 

Trying 127.0.0.1...
Connected to 
Escape character is '^]'.
220 ESMTP Sendmail 8.14.4/8.14.4/Debian-2ubuntu1; Fri, 21 Jun 2013 10:35:21 +0100; (No UCE/UBE) logging access from: (OK)-[127.0.0.1]
ehlo localhost
250-Hello [127.0.0.1], pleased to meet you
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-EXPN
250-VERB
250-8BITMIME
250-SIZE
250-DSN
250-ETRN
250-AUTH DIGEST-MD5 CRAM-MD5
250-STARTTLS
250-DELIVERBY
250 HELP

The emails are being delivered successfully. However, after sending emails the email logs do not show any entry for TLS.Also the message headers of the email do not contain information about TLS. 

Ubuntu details:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

Sendmail version: 8.14.4

Kindly suggest if we are missing something.

---

### Post by Riunixteam on 2013-06-27
Hi, 

Please check and suggest regarding this.

---

### Post by stmiller on 2013-06-29
Are you referring to SMTP-TLS?

I would suggest using postfix instead of sendmail. Postfix is far easier to configure.

Cheers,

---

### Post by Riunixteam on 2013-07-02
Ues SMTP-TLS. We cannot change the server setup. We have to use sendmail with TLS. Please suggest why the headers do not show TLS encryption. Does that mean that the server is not using TLS correctly?

---

### Post by SeijiSensei on 2013-07-02
If you can deploy another virtual server, I recommend you install a copy of CentOS 6.4 and install sendmail on that.  I don't usually have to do anything to get it to use TLS, though by default it uses a "snakeoil" cert in /etc/pki/tls.  You can replace that with your own certificate if you purhased one.

On the CentOS platform, I routinely install the [MailScanner]("http://www.mailscanner.info/") package that includes MailScanner itself, SpamAssassin, and ClamAV.  The default configuration scans every message for viruses with ClamAV and for spam with SpamAssassin.  The first are quarantined, while spam is quarantined or tagged and delivered depending on a message's SpamAssassin score.

My server shows log entries like these when it sends a message to a remote site that uses TLS:
```
Jul  2 19:04:20 xxxxx sendmail[31387]: STARTTLS=client, relay=gmail-smtp-in.l.google.com., version=TLSv1/SSLv3, verify=FAIL, cipher=RC4-SHA, bits=128/128
```

The failed verification comes from using a certificate not signed by a trusted root.  

However I don't see any inbound mail that uses TLS.  All our inbound mail arrives via ESMTP.  Here, for instance, is an inbound message from GMail:
```

Jul  2 08:10:11 xxxxx sendmail[30723]: r62CAB0K030723: from=<someone@gmail.com>, size=1783, class=0, nrcpts=1, msgid=CAEpVZbSPRgPEAURHyT=5QYhzin7A6_tuGfLxKq+Xc9VqcsSCFA@mail.gmail.com>, proto=ESMTP, daemon=MTA, relay=mail-vb0-f49.google.com [209.85.212.49]

```

Are you looking to configure sendmail to force remote sending servers to prefer TLS?  If so, [this](https://www.sendmail.com/sm/blog/wik/?p=1238) looks like a good starting point.

---

