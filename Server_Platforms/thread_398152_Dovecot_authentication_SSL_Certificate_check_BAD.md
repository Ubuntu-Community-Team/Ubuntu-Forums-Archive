---
title: "Dovecot authentication: SSL Certificate check: BAD"
date: 2007-03-31
forum: Server Platforms
---

### Post by knipknap on 2007-03-31
Hello,

Whenever a client connects to my Dovecot IMAP server, the following error message is displayed:

```
SSL Certificate check for 192.168.0.2:

Issuer:            E=root@knap,CN=knap,OU=Office for Complication of Otherwise Simple Affairs,O=OCOSA,L=Everywhere,ST=There is no such thing outside US,C=XX
Subject:           E=root@knap,CN=knap,OU=Office for Complication of Otherwise Simple Affairs,O=OCOSA,L=Everywhere,ST=There is no such thing outside US,C=XX
Fingerprint:       88:56:06:83:b4:1a:dd:5a:53:6e:84:d3:8f:65:0e:9e
Signature:         BAD

Do you wish to accept?
```

How can I update or replace this certificate? From googling I found that a "snakeoil" certificate should be used. I guess that is a local fake authority server, but I don't know how to use it.

Any hints?

-Samuel

---

### Post by rsermilik on 2007-04-01
This is not an error message but a service message telling you about the certificate on the server.
You can just accept it.
Changing to the openssl default snakeoil certificate doesn't change anything.

Take a look in the documents at [www.openssl.org](www.openssl.org)

---

