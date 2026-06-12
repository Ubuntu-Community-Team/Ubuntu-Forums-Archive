---
title: "aks root password at failsafe boot"
date: 2012-07-15
forum: Security
---

### Post by brancalessio on 2012-07-15
I noted that if I choose "failsafe" in grub then I get into a menu where I can choose to open a root shell.

The point is that no password is asked in order to open such root shell. In principle anyone with my computer at hands could gain root privileges.

My question is: is it sufficient to set a root password to avoid this issue?

Thanks for your answers!

---

### Post by tubbygweilo on 2012-07-15
Physical access to your kit trumps all, so keep your physical kit safe. Fail-safe access and physical access go together.

---

### Post by Cheesemill on 2012-07-15
Physical access = root access.

Even if you do set a root password it doesn't stop anyone from either booting from a Live CD and accessing your data or simply removing the drive and reading it from another machine.

The only way to prevent access to your data is to use encryption.

---

### Post by brancalessio on 2012-07-15
Thanks again for your answer!

So, you confirm that I should set a root password to prevent what I described.

As far as encryption is concerned, I completely agree (and do it).

> **Cheesemill said:**
> Physical access = root access.

Even if you do set a root password it doesn't stop anyone from either booting from a Live CD and accessing your data or simply removing the drive and reading it from another machine.

The only way to prevent access to your data is to use encryption.

---

### Post by Ms. Daisy on 2012-07-15
> **brancalessio said:**
> So, you confirm that I should set a root password to prevent what I described. Have a look at this, should answer your questions.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Short answer, no.

---

