---
title: "seahorse"
date: 2009-05-16
forum: Security
---

### Post by dk6452 on 2009-05-16
I've been playing a little bit with seahorse and was wondering how the backend works. 

Is the private key stored in plaintext on the file system?
Is the passphrase used to generate the private key?

---

### Post by atfrase on 2009-05-17
I believe the private key is stored on the system, but the passphrase you provided is used to encrypt the private key itself, so it's not in plaintext.  So in order to use the private key to decrypt or sign anything, you have to provide the passphrase to decrypt the private key, and then GnuPG can use the private key to decrypt/sign the data.

---

### Post by Nepherte on 2009-05-17
Actually, the generated private key (possibly) depends on a lot of things: your passphrase, the speed and interval with which you enter your password, other input device actions like moving your mouse, etc... and is encrypted with an algorithm like RSA.

---

