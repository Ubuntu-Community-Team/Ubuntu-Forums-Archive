---
title: "compiling &quot;sign&quot;"
date: 2009-11-11
forum: Security
---

### Post by cong06 on 2009-11-11
[Alex Pankratov](http://swapped.cc/sign/) has a file called sign.

Extracting it and running "make" gives this error:
```

isaac@phaff:~/Desktop/sign-1.0.7$ make
make -C src
make[1]: Entering directory `/home/isaac/Desktop/sign-1.0.7/src'
cc -Wall -DNDEBUG -g   -c -o pki.o pki.c
pki.c: In function ‘pubkey_parse_openssh_text’:
pki.c:148: warning: pointer targets in passing argument 1 of ‘uudecode_len’ differ in signedness
uue.h:6: note: expected ‘const char *’ but argument is of type ‘uchar *’
pki.c:156: warning: pointer targets in passing argument 1 of ‘uudecode’ differ in signedness
uue.h:7: note: expected ‘const char *’ but argument is of type ‘uchar *’
pki.c:156: warning: pointer targets in passing argument 3 of ‘uudecode’ differ in signedness
uue.h:7: note: expected ‘char *’ but argument is of type ‘uchar *’
pki.c: In function ‘pubkey_store_openssh_text’:
pki.c:194: warning: pointer targets in passing argument 1 of ‘uuencode’ differ in signedness
uue.h:10: note: expected ‘const char *’ but argument is of type ‘uchar *’
pki.c:194: warning: pointer targets in passing argument 3 of ‘uuencode’ differ in signedness
uue.h:10: note: expected ‘char *’ but argument is of type ‘uchar *’
pki.c: In function ‘prikey_parse_pem’:
pki.c:288: error: ‘EVP_F_EVP_DECRYPTFINAL’ undeclared (first use in this function)
pki.c:288: error: (Each undeclared identifier is reported only once
pki.c:288: error: for each function it appears in.)
pki.c:295: warning: pointer targets in assignment differ in signedness
make[1]: *** [pki.o] Error 1
make[1]: Leaving directory `/home/isaac/Desktop/sign-1.0.7/src'
make: *** [all] Error 2

```

A replacement for 'sign' is also an option, but at this point I don't know of any replacements in ubuntu. All I need is something to test a digital signature of a file. Unfortunately I'm not very familiar with digital signatures...

---

### Post by Sarmacid on 2009-11-11
You can verify PGP signatures in ubuntu, just need to import the private key with the passwords and encryption keys application and then right click the file on nautilus and select decrypt/verify.

---

### Post by cong06 on 2009-11-12
Do you have any ideas on scripting it though? I don't know the nautilus command for unsigning...

---

### Post by Sarmacid on 2009-11-12
You could check the CLI options of gpg for scripting```
gpg --help
man gpg
```

---

### Post by tubbygweilo on 2009-11-12
cong06,
An additional how to covering [Gnu Privacy Guard (GnuPG)]("http://www.dewinter.com/gnupg_howto/english/GPGMiniHowto.html") which may well anser some of you questions.

---

