---
title: "can't decrypt with openssl"
date: 2010-04-27
forum: Security
---

### Post by methodtwo on 2010-04-27
Hi i need to decrypt things with my privatekey using openssl:
As an example this is the command i'm using to try and decrypt things that were encrypted with my public key:
```
#openssl rsautl -decrypt -in encrypted.txt -out result.txt -inkey privatekey.pem
```
and this is the result that i get:
```
RSA operation error
17812:error:0406506C:rsa routines:RSA_EAY_PRIVATE_DECRYPT:data greater than mod len:/on10/build-nd/G10U4B0/usr/src/common/openssl/crypto/rsa/rsa_eay.c:393:
```
The private key is in my PATH.The results are the same on solaris and linux.What am i doing wrong?.How should i decrypt files with my privatekey(which is pem format and is the right value)
Thankyou for your time
regards mathodtwo

---

### Post by noway2 on 2010-04-28
It looks like it was encrypted with a different algorithm.  See this link:[http://www.mail-archive.com/openssl-users@openssl.org/msg53710.html](http://www.mail-archive.com/openssl-users@openssl.org/msg53710.html)

I googled the term "data greater than mod len openssl" and came up with several links to this error message.  Perhaps one of them will have a solution.

---

