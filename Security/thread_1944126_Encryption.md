---
title: "Encryption"
date: 2012-03-20
forum: Security
---

### Post by Jaybyrrd on 2012-03-20
I currently have two different hard drives, one of which is partitioned into two sections. The one not partitioned is my Ubuntu Drive, one of the partitions asks as a data dump, and the smaller partition asks as an OS Drive for Windows (I still game).

I currently want to encrypt all of them, however I want my windows drive to be encrypted, unless given a passphrase, to my Ubuntu install, and vice versa, furthermore I want the data dump to be encrypted and accessible from both OS's.

What do I do to make this happen as I am clueless.


Note my Ubuntu drive is already encrypted.

---

### Post by bubylou on 2012-03-20
Maybe [Truecrypt]("http://www.truecrypt.org/") is just what your looking for. It works on both Windows and Linux.

---

### Post by MasterGamerJK on 2012-03-20
decrypt your Ubuntu partition and use Truecrypt to encrypt the full disk. This will install a section into the boot loader of the book drive which will require a password before the systems event offers which OS to load.  ^_^

---

### Post by Jaybyrrd on 2012-03-20
Ugh, so I have to decrypt my current ubuntu... I might just reinstall... again. =/ too much work considering I hardly understand how i even encrypted to begin with, seems like this is solved though. Thanks guys!

---

### Post by MasterGamerJK on 2012-03-20
You would not HAVE to decrypt it by any means, its just best practice. My guess is that you clicked the "encrypt my home directory" when you installed in. In which case, don't worry about it.

---

