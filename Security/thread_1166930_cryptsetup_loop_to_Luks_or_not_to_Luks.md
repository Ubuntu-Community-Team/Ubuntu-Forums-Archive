---
title: "cryptsetup loop to Luks or not to Luks"
date: 2009-05-22
forum: Security
---

### Post by dstempfley on 2009-05-22
I've seen a number of examples of creating encrypted mappings to loopback file systems using cryptsetup. They vary between just setting up a mapping using the create option of cryptsetup and using luksFormat.  I have planned on using luksFormat, but are there criteria that one should use to decide which path is more correct for a particular application?

/Dion

---

### Post by HermanAB on 2009-05-22
Howdy,

The basic criteria for using encription should be the security level required.  Cryptoloop is not secure and can be cracked using simple XOR operations.  So it is good protection against your little kid sister - well, until she turns 12 maybe.

You can set LUKS up very easily.  Install luks-tools and use the gnome-luks-format wizard (run it as root with sudo).

---

### Post by dstempfley on 2009-05-27
Thx

---

