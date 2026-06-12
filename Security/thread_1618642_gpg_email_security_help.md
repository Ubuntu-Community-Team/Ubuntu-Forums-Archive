---
title: "gpg email security help"
date: 2010-11-10
forum: Security
---

### Post by amyfan on 2010-11-10
Hi guys and gals, i am running ubuntu 10.10 64bit.

when i  use gpg with thunderbird? i had a old key to my email address lost it about 3 months ago, then just now replaced it with a new one and when i try to decrypt a email i get this error 
now do note this is the security key i lost not the public key.


```
OpenPGP Security Info

Error - secret key needed to decrypt message

gpg command line and output:
/usr/bin/gpg
gpg: encrypted with 3072-bit ELG-E key, ID 254665CC, created 2010-08-30
      "soso email <sos@soso.soso>"
gpg: encrypted with ELG-E key, ID AADEA3B6
gpg: decryption failed: secret key not available 
```

---

### Post by movieman on 2010-11-10
Without the secret key, you can't decrypt the mail in the next million years or so.

---

### Post by amyfan on 2010-11-10
> **movieman said:**
> Without the secret key, you can't decrypt the mail in the next million years or so.

So there is no way i can make my new security key code work?

---

### Post by movieman on 2010-11-10
> **amyfan said:**
> So there is no way i can make my new security key code work?

Not to decrypt messages encrypted to the old key. You can use the new key for future emails, but the old messages are now just slightly non-random numbers.

Edit: and note that you need to ensure that anyone sending messages to you is now using the new key and not the old one.

---

