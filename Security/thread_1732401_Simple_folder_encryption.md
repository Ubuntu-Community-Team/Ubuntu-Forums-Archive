---
title: "Simple folder encryption?"
date: 2011-04-18
forum: Security
---

### Post by perrti-y02 on 2011-04-18
Hello,

I am looking for a way to encrypt, or secure in any other way, a folder on my computer.

I would be surprised if the folder ever got larger than 1GB so I would prefer not to make a file system and encrypt an entire partition.

The folder will be on my computer in a shared flat, so people have access to all my files. I am not trying to keep them from ever finding it, just make sure that they won't stumble upon this folder. It is also accessible from the internet by SSH but I don't think this is an issue since the SSH is secure anyway (but please correct me if I am wrong).

I would guess that the best way would be to use something like TrueCrypt and if this is the case I was wondering if anyone could explain more or less how it works, just from the perspective of wanting to learn.

Many Thanks

Tim

---

### Post by HermanAB on 2011-04-18
Cryptkeeper.  It is in the repos.

Otherwise, use Zip with a password.  It is integrated with Nautilus.  Just right click and select compress, zip, options, pasword.

---

### Post by sj1410 on 2011-04-19
truecrypt is good.

as it says it Creates a virtual encrypted disk within a file and mounts it as a real disk. Encrypts an entire partition or storage device such as USB flash drive or hard drive.............

more on........[http://www.truecrypt.org/](http://www.truecrypt.org/)

---

