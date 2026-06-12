---
title: "are encrypted files really secure? what if deleted?"
date: 2014-01-25
forum: Security
---

### Post by raspatan on 2014-01-25
Hi all. 

I encrypted my documents with Ecnfs as usual. My files are now encrypted and thus the folder with them dissapears if not mounted. However, it disturbs me that the folder with the encrypted data is always there (if hidden, still are there for anyone to see by using CTRL+H in Nautilus or Thunar or etc). Therefore, anyone could delete them, and even delete the .xml file, which apparently is crucial. In other words, I created a nice SELFTRAP where someone can DENY ME access to my files (even if that person cannot obtain them) by deleting the encrypted data. Given that many hacker attacks are actually interested in just destroying information, I cannot feel much safer now than before without encryption. 

Am I thinking incorrectly here and is there something I am not seeing? Is there a way to overcome this problem if exist? I imagine an infinite loop of encryptions is not a possible solution. 

Thank you!

---

### Post by raspatan on 2014-01-25
Is it that the encryption is in fact a safe way to **transfer** files rather than to **store** them? 

How to store files safely then? Cloud?

---

### Post by bashiergui on 2014-01-25
Encryption protects data stored. If I put data in some cloud I would encrypt it locally then send it to the cloud, so that would protect it from being sniffed while being transmitted and protect it at rest.

If you don't want people to access your encrypted files on your computer, then do not allow people to access the computer. If you have to let people use it, then maybe encrypted cloud storage would be better.

---

### Post by Dave_L on 2014-01-25
> **raspatan said:**
> In other words, I created a nice SELFTRAP where someone can DENY ME access to my files (even if that person cannot obtain them) by deleting the encrypted data.

I'm not sure what your question is.

The purpose of encryption is to hide information.

To protect against deletion of your files, back up your files.

---

### Post by ian-weisser on 2014-01-25
> **raspatan said:**
> Therefore, anyone could delete them, and even delete the .xml file, which apparently is crucial. In other words, I created a nice SELFTRAP where someone can DENY ME access to my files (even if that person cannot obtain them) by deleting the encrypted data.

+1 to Dave_L's comment.
Yes, if you fail to backup, you will eventually lose data.
Encryption, in this case, seems irrelevant. You can lose the data to flood or fire or theft or misplacement...or an attack.

Encryption only protects you from unauthorized access. It is not intended to prevent data loss. Backups prevent data loss.

---

