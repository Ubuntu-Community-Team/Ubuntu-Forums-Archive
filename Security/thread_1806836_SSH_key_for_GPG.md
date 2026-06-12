---
title: "SSH key for GPG"
date: 2011-07-18
forum: Security
---

### Post by w4rh4wk on 2011-07-18
Hello there,
First if all, please excuse me if i am posting in the wrong forum. The Mod will move the topic anyway, but sorry for the inconvenience.

I generated a ssh key pair to do my everyday work and recently found out about GPG. I want to use GPG to encrypt documents and important files.

- and i was wondering if it would be possible to use the already generated ssh key for GPG to encrypt (and decrypt) documents.

I already learned that it is possible to let the gpg agent manage the ssh key.

And i don't want to use openssl. As far as i know, openssl is there to encrypt streams not files (even if it would work for files too).

What are you suggesting.

---

### Post by psusi on 2011-07-18
No, it is not possible.  SSH uses a bare RSA key pair.  GPG uses digital certificates, of which key pairs ( RSA, DSA, or El Gammel ) are only a part.

You can of course, use the same password to encrypt the private key in both, but you will need to generate a new gpg certificate.

---

### Post by w4rh4wk on 2011-07-18
thank you for fast response and information

---

