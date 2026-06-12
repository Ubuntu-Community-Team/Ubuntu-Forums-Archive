---
title: "password reset protection"
date: 2012-01-17
forum: Security
---

### Post by goodbye-windows(tm) on 2012-01-17
Hi All,

If my home folder is encrypted, can the contents of it be examined by an unauthorized individual if they use the password reset command? Or, is the data locked down until the original password or passphrase is given??

I like the idea of encrypting the home folder, but just want to understand the benefits and liabilities.

TY.

Art

---

### Post by hackertarget on 2012-01-17
Encrypted home directories require the correct passphrase to be able to read them. This is by design. There is no back door (AFAIK :o).

[https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome)

---

### Post by bodhi.zazen on 2012-01-17
> **goodbye-windows(tm) said:**
> Hi All,

If my home folder is encrypted, can the contents of it be examined by an unauthorized individual if they use the password reset command? Or, is the data locked down until the original password or passphrase is given??

I like the idea of encrypting the home folder, but just want to understand the benefits and liabilities.

TY.

Art

Try it (in a VM) and see for yourself.

---

### Post by FuturePilot on 2012-01-18
> **goodbye-windows(tm) said:**
> Hi All,

If my home folder is encrypted, can the contents of it be examined by an unauthorized individual if they use the password reset command? Or, is the data locked down until the original password or passphrase is given??

I like the idea of encrypting the home folder, but just want to understand the benefits and liabilities.

TY.

Art

Your login password is used to create another password for encrypting your home directory. So, no, if someone reset your password they wouldn't be able view the contents of your home directory.

---

