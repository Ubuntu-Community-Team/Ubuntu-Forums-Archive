---
title: "gpg encrypt - openssl decrypt"
date: 2010-12-20
forum: Security
---

### Post by lavajumper on 2010-12-20
Has anyone been successful password encrypting files in gpg and then decrypting with openssl, and vice-versa. When decrypting with openssl, it complains 'bad magic number'. GPG complains that there is 'no valid OpenPGP data found', and never asks for a password.

```
openssl enc -k 1234 -cast5-cbc -in testopenssl.tar.gz -out testopenssl.tar.gz.gpg

gpg -d testopenssl.tar.gz.gpg > test.tar.gz

```

```
gpg -c testgpg.tar.gz

openssl enc -d -k 1234 -cast5-cbc -in testgpg.tar.gz.gpg -out test-gpg.tar.gz
```

I've also attempted this with aes128 and aes256 ciphers. I've also tried -cast, -cast5-cfb, -cast5-ecb, -cast5-ofb switches and numerous other 'sane' switches. The encrypted files decrypt successfully if I use the program that performed the encryption.


We are trying to encrypt files for archiving, and would like the archives to be as portable as possible.

---

### Post by sanderd17 on 2010-12-20
If you could decrypt it with an other algorithm, the encryption wouldn't be a real encryption. So it's not possible.

---

### Post by lavajumper on 2010-12-20
No, I'm using the same algorithms. At least I'm trying to. 
The cast5 is a bit confusing in openssl, which is why I why I attempted every cast5-xxx entry available in openssl. And also why I ran tests using aesXXX ciphers.

---

### Post by lavajumper on 2010-12-27
Maybe I'm missing something. If I use openssl to password encrypt a file using aes256 encryption algorithm, I thought it would be possible to decrypt the file using gpg, telling gpg to decrypt using the aes256 algorithm ( gpg --decrypt --cipher-algo aes256 testfile.enc > testfile.txt )

Can anyone explain what I might be doing wrong, or if I'm simply missing the big picture?

---

