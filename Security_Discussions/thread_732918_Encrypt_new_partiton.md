---
title: "Encrypt new partiton?"
date: 2008-03-23
forum: Security Discussions
---

### Post by Dr Small on 2008-03-23
So I have Ubuntu installed, have alot of space on the hard drive, and wanted to make a new partition and encrypt it with a password / keyfile, but not have it auto mount at bootup.

Any good pointers to do this?

Dr Small

---

### Post by update_manager on 2008-03-23
> **Dr Small said:**
> So I have Ubuntu installed, have alot of space on the hard drive, and wanted to make a new partition and encrypt it with a password / keyfile, but not have it auto mount at bootup.

Any good pointers to do this?

Dr Small

[http://www.truecrypt.org/](http://www.truecrypt.org/)

When encrypted, the container looks like a file. When decrypted, it will appear as its own device/partition (a lot like a USB key).

You could also use encfs (check out this GUI [http://www.getdeb.net/app/Cryptkeeper](http://www.getdeb.net/app/Cryptkeeper)) however I don't think you'd have keyfile support.

---

### Post by Dr Small on 2008-03-23
Hmm, well, I have used Truecrypt in the past, and I know it creates a file.
I was thinking more along the lines of creating a new partition with gParted and then encrypting it, mounting it via the terminal, (entering a password), move files to the partition, and unmounting it.

But I'll take a look at encfs to see what all it can do.

Dr Small

---

### Post by thewanderer on 2008-03-24
[TrueCrypt]("http://www.truecyrpt.org") can also encrypt a full partition.

> Main Features:

    * Creates a virtual encrypted disk within a file and mounts it as a real disk.

    * Encrypts an entire partition or storage device such as USB flash drive or hard drive.

---

