---
title: "Question on gpg encryption with a symmetric cipher!"
date: 2009-07-01
forum: Security
---

### Post by Rytron on 2009-07-01
Hi.
Using a passphrase that is 27 characters long and includes lower & upper case letters,special characters and numbers, how secure would a file be if it was encrypted with this method:
gpg -c file_one

---

### Post by HermanAB on 2009-07-01
Howdy,

The default GPG cypher is Cast5 (a.k.a. Cast128).  It is still secure as far as I know, although Cast256 is recommended nowadays.

---

### Post by Dr Small on 2009-07-01
Why limit yourself to 27 characters? Come on... 64 characters is better, lol :)

---

### Post by kevdog on 2009-07-01
I thought the default cipher type was AES128.  I could be wrong however.  I know the default sdk cipher is cast5.

I would recommend for your use AES256 for your encryption cipher-type.  Its been very well tested.  3DES is also good, however slightly slower.  In fact if I'm not mistaken, 3DES is the default cipher according to the OpenGPG standard.

Anyway, to see what ciphers you have available, type:
gpg -v -version

To use one of the ciphers in the list:
gpg --symmetric --cipher-algo <CIPHER_ALGO> <filename>

---

