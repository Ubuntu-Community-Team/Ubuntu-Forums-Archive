---
title: "gpg --sign archive.tar.gz Can you extract the data without the public key."
date: 2017-06-06
forum: Security
---

### Post by cherva on 2017-06-06
I am looking into making a secure upgrade system.
The idea is to give a file to a client running my software. Then he uploads it to his HW device via http on his local network... much like upgrading wifi routers....
Looking at GPG for signing a password protected tar.gz archive.....
[https://www.gnupg.org/gph/en/manual/x135.html]("https://www.gnupg.org/gph/en/manual/x135.html")

I will have the archive's password on the device. I know brute forcing is an option, so I will sign the archive with a private key.
```
gpg --sign archive.tar.gz
```
My question is IF it put the public key on the device and do NOT redistribute it...
Can the produced signed file be reversed to the original password protected tar.gz file without the public key ?

---

### Post by cherva on 2017-06-07
Anyone ?

---

### Post by bashiergui on 2017-06-09
If you're encrypting the archive and using asymetric keys to encrypt/decrypt, then the only way to get the password is to have the private key.

---

