---
title: "Accessing NTFS-encrypted Files and Folders"
date: 2010-05-14
forum: Security
---

### Post by user2037 on 2010-05-14
After trying Truecrypt, LUKS, and Ecryptfs I decided to try NTFS encryption. Now, on a dual boot computer from Ubuntu I can browse the encrypted folders but can not open the encrypted files. All attempts produce access denials yet the Unix file permissions appear to be "0777" (owner, group, and world readable-writable).

Is there someway to get Ubuntu's NTFS software to recognize and decrypt the encrypted files? Would a different NTFS package work such as NTFS-3g?

---

### Post by jerome1232 on 2010-05-14
NTFS-3G doesn't fully support ntfs encryption yet. As far as I know nothing for linux does.

[http://www.tuxera.com/community/ntfs-3g-faq/#compressed](http://www.tuxera.com/community/ntfs-3g-faq/#compressed)

---

### Post by HermanAB on 2010-05-15
If you want cross platform encryption, then you should use LUKS and FreeOTFE or TrueCrypt.

---

