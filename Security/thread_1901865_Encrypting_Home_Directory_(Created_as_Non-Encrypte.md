---
title: "Encrypting Home Directory (Created as Non-Encrypted)"
date: 2011-12-29
forum: Security
---

### Post by noloader on 2011-12-29
Hi All,

I'm using Ubuntu 10.04 and 11 (the flavor where I can disable Unity). I'm interested in encrypting my home directory after the fact (the account was originally created without encryption).

Encrypted Filesystem HowTo was the third hit on a search for 'Ubuntu encrypt home directory" (the first two were noise). Is[ EncryptedFilesystemHowto]("https://help.ubuntu.com/community/EncryptedFilesystemHowto?action=fullsearch&context=180&value=linkto%3A%22EncryptedFilesystemHowto%22") ([https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)) applicable and up to date?

It seems like a heck of a lot of [manual] work. I find it a bit surprising, since Microsoft (Windows) and Apple (Mac OS) have been doing it for years. Perhaps there's a different document I should be using?

Jeff

---

### Post by Dave_L on 2011-12-29
The script ecryptfs-migrate-home is an easier way. It's included in the package ecryptfs-utils.

[http://blog.dustinkirkland.com/2011/02/long-overdue-introduction-ecryptfs.html](http://blog.dustinkirkland.com/2011/02/long-overdue-introduction-ecryptfs.html)

I used it successfully on 10.04.

---

