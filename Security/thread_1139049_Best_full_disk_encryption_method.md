---
title: "Best full disk encryption method?"
date: 2009-04-26
forum: Security
---

### Post by lurikeen on 2009-04-26
I'm looking to encrypt my entire disk, including the swap file. I was disappointed when I realized that truecrypt doesn't offer full disk encryption for linux.

What would you guys recommend I use for to do this? I don't care about /boot being visible (since I'm fairly certain this cannot contain sensitive data), or even if someone can tell that it is encrypted. I just want something strong and fast, like AES for example.

---

### Post by radar2020 on 2009-04-26
For full disk encryption I installed with the 8.10 alternate CD.

Everything is encrypted except /boot.

---

### Post by lurikeen on 2009-04-26
Do you know anything about the encryption scheme? Name, algorithm, ect?

---

### Post by HermanAB on 2009-04-26
Howdy,

LUKS with AES256.  Google for details.

---

