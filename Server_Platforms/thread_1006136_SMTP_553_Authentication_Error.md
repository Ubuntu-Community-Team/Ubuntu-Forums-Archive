---
title: "SMTP 553 Authentication Error"
date: 2008-12-09
forum: Server Platforms
---

### Post by paulpc on 2008-12-09
I've setup a LAMP server, and I need to programatically send emails out to the world. The server is a virtual machine, and has a DHCP assigned IP address. There's no domain name.

I've followed the postfix setup instructions from the Ubuntu official documentation, but when I send mail, I get the following response from my ISP's mail server:

Dec  9 12:19:03 Develop postfix/qmgr[4797]: B3660EDA82: from=<paul@bigpond.net.au>, size=341, nrcpt=1 (queue active)
Dec  9 12:19:04 Develop postfix/smtp[4870]: B3660EDA82: to=<pcn@bigpond.net.au>, relay=extmail.bpbb.bigpond.com[61.9.189.122]:25, delay=0.91, delays=0.06/0.02/0.79/0.04, dsn=5.0.0, status=bounced (host extmail.bpbb.bigpond.com[61.9.189.122] said: 553 Authentication is required to send mail as <paul@bigpond.net.au> (in reply to MAIL FROM command))
Dec  9 12:19:04 Develop postfix/cleanup[4867]: A1B4227BB7: message-id=<20081209021904.A1B4227BB7@develop.bigpond.net.au>
Dec  9 12:19:04 Develop postfix/qmgr[4797]: A1B4227BB7: from=<>, size=2310, nrcpt=1 (queue active)
Dec  9 12:19:04 Develop postfix/bounce[4871]: B3660EDA82: sender non-delivery notification: A1B4227BB7
Dec  9 12:19:04 Develop postfix/qmgr[4797]: B3660EDA82: removed
Dec  9 12:19:05 Develop postfix/smtp[4870]: A1B4227BB7: to=<paul@bigpond.net.au>, relay=extmail.bpbb.bigpond.com[61.9.189.122]:25, delay=0.6, delays=0.03/0/0.52/0.05, dsn=5.0.0, status=bounced (host extmail.bpbb.bigpond.com[61.9.189.122] said: 550 Invalid recipient: <paul@bigpond.net.au> (in reply to RCPT TO command))
Dec  9 12:19:05 Develop postfix/qmgr[4797]: A1B4227BB7: removed

/etc/postfix/main.cf includes:
myhostname = develop.bigpond.net.au
mydestination = mail.bigpond.com,localhost.localdomain,localhost
mynetworks = 127.0.0.0/8, 192.168.0/255
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls = yes


Can anyone help me with this?

Many Thanks,

Paul

---

### Post by stiV on 2008-12-09
Your LAMP is trying to send emails using the sender mail address "paul@bigpond.net.au".

The SMTP-Server of your recipient is responsible for @bigpond.net.au and does not permit unauthenticated sending with "his" domain.

The easiest way would be to set the sending emailaddress to something else - or activate SMTP authentication in LAMP (this should be possible i guess)

that line tells you the story ;)

Host extmail.bpbb.bigpond.com[61.9.189.122] said: 553 Authentication is required to send mail as <paul@bigpond.net.au> (in reply to MAIL FROM command))

---

### Post by paulpc on 2008-12-09
The documentation I referred to includes setting up SMTP authentication. I followed their instructions exactly, but I'm still getting the 553 authentication error.

---

