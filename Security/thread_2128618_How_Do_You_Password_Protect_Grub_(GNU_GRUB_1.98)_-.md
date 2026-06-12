---
title: "How Do You Password Protect Grub (GNU GRUB 1.98) - Not GRUB2"
date: 2013-03-23
forum: Security
---

### Post by charliemp3 on 2013-03-23
I have been looking for information on how to password protect Grub (GNU GRUB 1.98), I'm not on Grub2. I did find the document for Grub2 but it does me no good.

I have also searched several other sites for clues on how to do this but most point to other Linux flavors.

Does anyone here know how to do this for Ubuntu? I would appreciate any help you can give me. I just need to setup an admin password to protect menu entries in Grub, but I'm lost.

Thank you.

By the way I'm on Ubuntu 10.04 LTS, and I can't yet upgrade to a later release.

---

### Post by deadflowr on 2013-03-23
[https://help.ubuntu.com/community/Grub2/Passwords](https://help.ubuntu.com/community/Grub2/Passwords)

Grub 1.98 is grub2

grub is 0.97, or so.

---

### Post by Stonecold1995 on 2013-03-23
I wouldn't suggest setting a password for GRUB if the password is of any importance.  Because the hash of the password is stored in plain site, anyone could get it and try to brute-force it, and because it uses the MD5 hashing algorithm, it is rather weak.  Not only that, but it's not that hard to bypass the password by going into GRUB command line.

If you really want to secure your computer, consider disk encryption.

---

