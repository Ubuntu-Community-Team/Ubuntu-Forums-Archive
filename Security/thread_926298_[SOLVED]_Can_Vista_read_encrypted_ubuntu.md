---
title: "[SOLVED] Can Vista read encrypted ubuntu?"
date: 2008-09-21
forum: Security
---

### Post by slughappy1 on 2008-09-21
I have a dual boot system. I have Ubuntu installed with an encrypted lvm. I have a desktop computer and has Ubuntu and Vista installed. I was able to install something that allows Vista to be able to access the Linux partitions. But I'm not sure if there is anything that would allow me to access my encrypted partitions.

I [originally_posted]("http://ubuntuforums.org/showthread.php?t=926188") in the beginners forum, but the only reply I got was to post here.

---

### Post by Bios Element on 2008-09-21
Well I'd assume "encrypted" would be designed to keep people out. So i'm guessing it couldn't.

---

### Post by Dr Small on 2008-09-21
In short; If it is encrypted, then Vista nor any other OS can read it, without first decrypting it.

---

### Post by kevdog on 2008-09-21
How did you encrypt it?

Windows has TrueCrypt, GPG encryption available, but if you are using LUKS encryption, the answer would be no!

---

### Post by slughappy1 on 2008-09-21
I used what is on the Ubuntu Alternate Disc, which is LUKS. So I take it from what kevdog said, I can't. Well that sucks. Luckily I just did a whole reinstall of everything on my computer. So I guess I will go about installing Ubuntu using TrueCrypt.

---

### Post by Uchiha_madara on 2008-09-22
I tried it Before it could not work ...

---

### Post by kevdog on 2008-09-22
I dont think Ubuntu can be installed with TrueCrypt as it can be with LUKS.  That is whole disk encryption, truecrypt is a partition encryption scheme.  The two are different.

---

### Post by hyper_ch on 2008-09-22
TC can also be used as full disk encryption (on windows)

---

### Post by slughappy1 on 2008-09-22
Well I used the Ubuntu Alternate CD to encrypt the partition. I put the root, swap, and home partition in an encrypted lvm. But this time I made a 40 GB FAT 32 extra partition. So now if I choose I can use TrueCrypt to encrypt Windows Vista and/or the extra partition.

---

### Post by doug-M on 2008-09-27
Supposedly FreeOTFE can read LUKS encrypted partitions from Windows.
Haven't tried it myself though.

[http://www.freeotfe.org/](http://www.freeotfe.org/)

[http://en.wikipedia.org/wiki/FreeOTFE](http://en.wikipedia.org/wiki/FreeOTFE)
"This software is compatible with Linux encrypted volumes (e.g. LUKS, cryptoloop, dm-crypt), allowing data encrypted under Linux to be read (and written) freely. It was the first open source transparent disk encryption system to support Windows Vista and PDAs"

---

