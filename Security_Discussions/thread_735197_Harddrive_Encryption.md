---
title: "Harddrive Encryption"
date: 2008-03-25
forum: Security Discussions
---

### Post by whirley on 2008-03-25
Hi I have an external hardrive using Ubuntu 7.10.

I would like to encrypt this drive but it has an NTFS file system with files on it.

Is this possible?

---

### Post by Dr Small on 2008-03-25
Encrypting the drive will erase the files that are on it.

---

### Post by picopir8 on 2008-03-25
If you encrypt the drive directly you will loose the file system and all files on it.

However, you could create an encrypted image and put it on the NTFS drive.  The image is a file and can reside on any file system, but can then be mounted much like mounting an ISO file.  Mounting requires a passphrase to decrypte but once mounted it will reveal another file system which you can access just like it were a physical drive.

It is pretty easy to set up but there are a fair amount of steps to follow.  The O'Reilly book "Ubuntu Hacks" provides a good walkthrouh on creating encrypted images.

The only downfall is that while you will be able to access the NTFS drive on a Windows computer, I am unaware of any way to mount the encrypted image under windows.  So any files inside the image will be inaccessible.

---

### Post by hyper_ch on 2008-03-26
> **Dr Small said:**
> Encrypting the drive will erase the files that are on it.
Not necessarily... truecrypt can in windows encrypt the whole system on the file... not sure whether it can also do it with an external partition...

as it is a ntfs drive I guess you'd rather want to use Truecrypt for encryption as tc is available for windows and linux.

---

