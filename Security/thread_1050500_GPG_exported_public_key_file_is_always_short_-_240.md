---
title: "GPG exported public key file is always short - 2405 bytes"
date: 2009-01-25
forum: Security
---

### Post by mgol on 2009-01-25
I see that many users of launchpad (and not only) are using quite long pgp public keys. For example, sabdfl has uploaded a file as big as 62762 bytes:
[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x5D3CE77FD54F0847](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x5D3CE77FD54F0847)

I tried to generate gpg key using:
```
gpg --gen-key
```
and then export it using:
```
gpg --export -a -o public_key.txt <name>
```

Even if I choose 4096 ELG-E keysize, which is maximum, I get a public file sized only 2405 bytes, which is quite small, compared to what others have.

How to make it bigger? Thanks a lot.

---

### Post by kevdog on 2009-01-25
4096 bits specification has nothing to do with the actual file size (which is in bytes).  I'm not sure how to explain it any clearer than that.

---

### Post by mgol on 2009-01-25
OK, I understand it, but is the exported signature safe despite being so small? Some people upload really huge ones; they probably have some reason to do that...

---

### Post by Dr Small on 2009-01-25
Embeding photos in the public key will also make it longer. (Maybe I'm not talking about the right thing here!)

---

### Post by kevdog on 2009-01-26
Maybe the appropriate place to ask this question is the GnuPG mailing list.  The whole security risk of GnuPG hinges on the private key, and not the public.  The public key is only able to encrypt messages to you, and provide verification of your signature.  Decryption and the ability to sign are properties of the private key.  Dr. Small is correct.  Its possible to embed photos within the private key which then become part of the public key.

---

