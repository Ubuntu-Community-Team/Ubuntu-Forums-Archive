---
title: "Encryption Question (truecrypt)"
date: 2009-06-05
forum: Security
---

### Post by uberlube on 2009-06-05
Just curious if it is possible to create an encryption (a container that takes up a whole partition or encrypting the whole partition itself) for my media partition without having to format it. I dont have any other medium to transfer my files to and id really hate to lose 100 gb worth of files.

---

### Post by picopir8 on 2009-06-05
I have not used truecrypt for at least a year now, but if my memory serves me correctly, it does not populate the container as it creates it. So if you want a container to be the size of you entire drive, then that entire drive needs to be empty.

---

### Post by pauna on 2009-06-05
> **uberlube said:**
> Just curious if it is possible to create an encryption (a container that takes up a whole partition or encrypting the whole partition itself) for my media partition without having to format it. I dont have any other medium to transfer my files to and id really hate to lose 100 gb worth of files.

Windows Vista version of Truecrypt has that feature, but not others.

If you don't specifically require Truecrypt, you could try LUKS. It has in theory the capability to do in-place encryption. The process isn't easy but some documentation is in [https://help.ubuntu.com/community/EncryptedFilesystemHowto7](https://help.ubuntu.com/community/EncryptedFilesystemHowto7)

---

