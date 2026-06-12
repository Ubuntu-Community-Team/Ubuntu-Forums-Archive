---
title: "Can someone explain a bit about these ssl prompts?"
date: 2011-10-17
forum: Server Platforms
---

### Post by trongbang on 2011-10-17
Hi guys,
My knowledge about SSL is quite limited except the fact that I know we have a private key and a public key. But I'm not very sure about CA certificate things like that. My question is can you please explain how those things are used in the following :

> 
touch smtpd.key
chmod 600 smtpd.key
openssl genrsa 1024 > smtpd.key
openssl req -new -key smtpd.key -x509 -days 3650 -out smtpd.crt # has prompts
openssl req -new -x509 -extensions v3_ca -keyout cakey.pem -out cacert.pem -days 3650 # has prompts

What is private key, public key and thing like that?

Thanks,

---

