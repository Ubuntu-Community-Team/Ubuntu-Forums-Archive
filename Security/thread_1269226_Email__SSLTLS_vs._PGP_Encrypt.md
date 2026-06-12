---
title: "Email:  SSL/TLS vs. PGP Encrypt"
date: 2009-09-18
forum: Security
---

### Post by timzak on 2009-09-18
Hi, I'm trying to understand something regarding email encryption.  I know that using PGP encryption would scramble email content so that only an authorized recipient could decrypt it, but what about the SSL/TLS protocols that, for example, Gmail supports?  Do these also offer a measure of encryption so that intercepted emails would be gibberish?  

In other words, if one uses SSL/TLS in their email, would using PGP encryption be redundant?

---

### Post by kevdog on 2009-09-18
SSL/TLS encrypts the transport, whereas PGP encrypts the content.  I'm not sure of your question or how to answer it appropriately since the two do two different things.  They might be redundant given your situation.  One thing is certain that your email most likely sits on Google's servers unencrypted ripe for a court supena.

---

### Post by Mister.Vash on 2009-09-18
SSL and TLS are done at the network level and just encrypt the transport stream.  Many servers do support it, but it's not something that you can control so you can't count on it being available for every hop.  So your message remains the same, it's just the network communications that would be encrypted provided at each hop, both sending and receiving machines support it/have it enabled.

PGP is used to encrypt the content.  Content encryption is what you would want to use to be sure that only the recipient would be able to read the message.

---

### Post by timzak on 2009-09-18
> **kevdog said:**
> SSL/TLS encrypts the transport, whereas PGP encrypts the content.

That's what I was getting at with my question.  Thank you both for your elegant answers!

---

