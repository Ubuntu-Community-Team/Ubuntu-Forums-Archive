---
title: "Encrypt IMAP storage backend?"
date: 2010-12-17
forum: Server Platforms
---

### Post by isync on 2010-12-17
I've always wondered if it is possible to encrypt the storage part of an IMAP mail installation.

Keeping your mails on a central server is very convenient if you access and manage mail via different devices. Still, what worries me is that all of my emails are kept plain-text on this central server! So anyone with (root) access to that server can read my mail! Unbearable.

Is there a way that my mailbox remains encrypted. And is only decrypted on the fly when I connect with a valid password to it?

Any suggestions, best practice, things-to-keep-in-mind?

---

### Post by HermanAB on 2010-12-17
Howdy,

The only way to keep your mail store secure, is to run your own mail server, for example [http://citadel.org](http://citadel.org).

---

### Post by isync on 2010-12-18
So there's actually no way/best-practice to encrypt IMPA storage backends??

I need to build a system where users get 100% privacy and even the sysadmin can't peek into their data.

It's there with hashed passwords in usermanagement (you never store plaintext-passwords but only the hashes of passwords a user supplies),
I can't believe it's not there in email...

---

