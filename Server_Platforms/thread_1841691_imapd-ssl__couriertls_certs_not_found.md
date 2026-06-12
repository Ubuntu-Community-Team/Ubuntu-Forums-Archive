---
title: "imapd-ssl  couriertls certs not found"
date: 2011-09-09
forum: Server Platforms
---

### Post by lister171254 on 2011-09-09
I'm running 11.04 64bit and have had my mail server running for more than six months. After the latest update(s) I get the following error when connecting mail clients with TLS.

>> imapd-ssl: couriertls: /etc/ssl/certs/c0cafbd2.0: No such file or directory

I've checked my config and nothing changed including the .pem in use.

testing via ssl returns with an error

>> openssl s_client -connect MyServer:993   
CONNECTED(00000003)
write:errno=104
>>

---

### Post by lister171254 on 2011-09-09
googled the cert in question and found it was for DigiNotar_Root_CA.

Followed this link [http://www.danielveazey.com/linux/how-to-remove-the-diginotar-root-ca-certificate-in-ubuntu/](http://www.danielveazey.com/linux/how-to-remove-the-diginotar-root-ca-certificate-in-ubuntu/)

All good now

---

