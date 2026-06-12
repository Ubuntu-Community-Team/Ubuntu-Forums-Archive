---
title: "How to upgrade GPG"
date: 2009-10-12
forum: Security
---

### Post by kiridude on 2009-10-12
Hi all.

By default i have GnuPG 1.4.9 and would like to upgrade to the latest 2.0.13 or at least 1.4.10. Is there a repository for GPG - I could not find a reference for GPG repository - or do I have to install from scratch?

Thanks.

---

### Post by kevdog on 2009-10-12
I would install from source.  As far as the difference between 1.xxx and 2.xxx I would stick with the 1.xx version. The 2.0xx version is no different other than the libraries are linked dynamically rather than statically.  You get no more increased functionality with this version.

To be honest, unless there is a big need to update, you are not going to get much.  Newer gpg versions have enabled the camellia cipher (which unless you live in Japan you probably don't use), and enable RSA rather than DSA keys as default.  You can do this with the older versions, although this is not the default settings.

---

### Post by kiridude on 2009-10-12
Thanks for your reply Kevdog. i am trying to make a 4096 key, but version 1.4.9 seems to offer a maximum of 2048.

Maybe I am not doing something correctly. In the key creation process, I enetered 4096, but only the elgamal subkey was 4096 bits. The primary DSA key was only 1024.

Is it possible to generate a 4096 bit key with this version of gpg?

Thanks

---

### Post by rookcifer on 2009-10-12
> **kiridude said:**
> Thanks for your reply Kevdog. i am trying to make a 4096 key, but version 1.4.9 seems to offer a maximum of 2048.

Maybe I am not doing something correctly. In the key creation process, I enetered 4096, but only the elgamal subkey was 4096 bits. The primary DSA key was only 1024.

Is it possible to generate a 4096 bit key with this version of gpg?

Thanks

```
gpg --gen-key --expert
```

I recommend creating an RSA key for both signing and encryption (option 7).  RSA is now the "standard" that is going to be used in future versions of gpg because of the possible compromise of SHA-1 (RSA can use stronger hash functions).

---

### Post by kiridude on 2009-10-12
> **rookcifer said:**
> ```
gpg --gen-key --expert
```

I recommend creating an RSA key for both signing and encryption (option 7).  RSA is now the "standard" that is going to be used in future versions of gpg because of the possible compromise of SHA-1 (RSA can use stronger hash functions).

Thank you Rookcifer, that did the trick! I was under the impression that I had to use a newer edition to achieve that.

---

