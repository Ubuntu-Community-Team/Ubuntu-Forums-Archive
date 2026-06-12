---
title: "Apache2 with and without SSL"
date: 2010-08-31
forum: Server Platforms
---

### Post by alfmarius on 2010-08-31
I managed to get apache2 working with SSL (creating the necesary files **server.crt**, **server.csr** and **server.key**) and dropped the following lines into **sites-available/default**:

```
SSLEngine on
SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
SSLCertificateFile /etc/apache2/ssl/server.crt
SSLCertificateKeyFile /etc/apache2/ssl/server.key
```[https://localhost](https://localhost) works fine now, however [http://localhost](http://localhost) gives an error:

```
**Bad Request**

 Your browser sent a request that this server could not understand.
Reason: You're speaking plain HTTP to an SSL-enabled server port.
Instead use the HTTPS scheme to access this URL, please.
...
```How can I get the apache2 server to respond to both https **and **http?

---

### Post by CharlesA on 2010-08-31
How did you enable SSL?

I had to use the directions listed here: [https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/77675](https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/77675)

Comments #60 and #61

Mine works for both http and https.

---

### Post by alfmarius on 2010-09-01
Well, seems I did a lot of unnecesary work. Ubuntu came with some certificates, so I undid everything previously and just ran these two

```
a2enmod ssl
a2ensite default-ssl
```and now both works.

that link you send me led me to** /usr/share/****doc/apache2.****2-common/****README.****Debian.****gz** which gave me a better understanding of this subject


thanks![B] :)
[/B]

---

