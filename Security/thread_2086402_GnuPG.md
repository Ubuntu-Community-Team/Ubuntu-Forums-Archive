---
title: "GnuPG"
date: 2012-11-20
forum: Security
---

### Post by Seeked on 2012-11-20
Hello Everybody,

When you are using GnuPG (gpg) to symmetrically encrypt a file the default algorithm is CAST5. 

When I am using gpg with Evolution to send encrypted emails, the actual message is encrypted with a symmetrical algorithm and the asymmetrical encryption (public/private keys) is used to encrypt the key for the symmetrical encryption.  My question is: What is the symmetrical algorithm that actually encrypts the message?  Is it CAST5 as well?

Thank You

---

### Post by Seeked on 2012-11-21
When I use:
~$: gpg --edit-key KEYID

You can then use:
gpg> pref
This will list the order of preferred algorithms for the key.  For all the keys I examined, even other people's public keys, the preferred algorithm was AES256 (S9).  

Use to set the order :
gpg> setpref S10 S9 S8 S7 S3 S2 H8 H2 H9 H10 H11 Z2 Z3 Z1

I found this page exceptionally helpful...
[http://pthree.org/2009/06/08/gnupg-up-and-close/](http://pthree.org/2009/06/08/gnupg-up-and-close/)

---

