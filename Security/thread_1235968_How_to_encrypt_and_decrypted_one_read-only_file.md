---
title: "How to encrypt and decrypted one read-only file?"
date: 2009-08-09
forum: Security
---

### Post by wolfv6 on 2009-08-09
[LEFT]                                  [LEFT][FONT=Times New Roman, serif][SIZE=3]Is there a simple way to encrypt  and decrypted just one read-only file?  I don't want to encrypt the entire file system.  This is the only file I want to encrypt.
[/SIZE][/FONT]
[FONT=Times New Roman, serif][SIZE=3]Thank you
[/SIZE][/FONT]
[/LEFT]
[/LEFT]

---

### Post by HermanAB on 2009-08-09
Here you go:
$ gpg -c filename

---

### Post by running_rabbit07 on 2009-08-09
Either what Herman said or just right click and scroll to the encrypt command.

---

### Post by kevdog on 2009-08-09
Symmetric encryption with gpg is probably the best solution as hermanab mentioned.  GnuPG is compatible on windows/linux/mac platforms, so you should be good to go.

---

### Post by running_rabbit07 on 2009-08-10
> **kevdog said:**
> Symmetric encryption with gpg is probably the best solution as hermanab mentioned.  GnuPG is compatible on windows/linux/mac platforms, so you should be good to go.

Is that the same program that right-clicking uses or is it another program that has to be installed?

---

### Post by wolfv6 on 2009-08-10
Thank you for your help.

---

