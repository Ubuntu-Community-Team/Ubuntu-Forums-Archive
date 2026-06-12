---
title: "Postfix SASL problem"
date: 2010-11-27
forum: Server Platforms
---

### Post by megabuffen on 2010-11-27
Hi everyone,

I'm running a server with Ubuntu 10.04 and I have installed postfix and courier. The server can recieve mail and I can fetch them using POP, but when I try to send mail it doesn't work. Postfix itself can send email if i telnet from localhost and I am using my ISP as a relay because they block port 25. I'm using outlook 2007 on my client computer and it just says that the server rejects the login attempt and tells me to check my username and password.

Postfix listens on port 12 as well because the client connection also has outgoing on port 25 blocked. I have tried to use telnet to connect to the server, and I can connect. This is what I get:

220 megabuffen.dyndns.org ESMTP Postfix (Ubuntu)
ehlo localhost
250-megabuffen.dyndns.org
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-STARTTLS
250-AUTH DIGEST-MD5 PLAIN LOGIN CRAM-MD5
250-AUTH=DIGEST-MD5 PLAIN LOGIN CRAM-MD5
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

Now what? I've tried searching for the answer but all I can come up with is AUTH PLAIN or AUTH LOGIN, but I don't know what to type after that.

Does anyone know what's wrong and if not, how can I find out?

---

### Post by lisati on 2010-11-27
Do you have TLS/Starlis enabled on your email client?

---

### Post by megabuffen on 2010-11-27
I don't know what starlis is, so I suppose not, and I'm not using TLS.

---

