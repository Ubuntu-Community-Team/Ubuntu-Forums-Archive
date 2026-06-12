---
title: "Secure file shredding..."
date: 2006-08-25
forum: Server Platforms
---

### Post by andy_fac51 on 2006-08-25
I am a newbie to the world of Linux (Now that Windows Vista has come out, my XP Machine is outdated), I would like to know how I can shred files in Linux. I deal with alot of personal and sensitive data on a day to day basis.

---

### Post by Dr. Nick on 2006-08-25
try here for a few ideas
[http://ubuntuforums.org/showthread.php?t=204667&highlight=secure+delete](http://ubuntuforums.org/showthread.php?t=204667&highlight=secure+delete)

---

### Post by az on 2006-08-25
> **andy_fac51 said:**
> I deal with alot of personal and sensitive data on a day to day basis.

[https://help.ubuntu.com/community/EncryptedFilesystem](https://help.ubuntu.com/community/EncryptedFilesystem)

---

### Post by matthew on 2006-08-25
There's a "shred" command already installed on your system as part of the GNU Core Utilities package that comes standard in Ubuntu. To learn how to use it open a terminal and type
```
man shred
```
and see if you will find it useful

---

### Post by skymt on 2006-08-28
> **azz said:**
> [https://help.ubuntu.com/community/EncryptedFilesystem](https://help.ubuntu.com/community/EncryptedFilesystem)

Not a good idea. Makes it too easy to lose everything, including your non-sensitive data, if something goes wrong. Use [TrueCrypt](http://www.truecrypt.org/) instead.

---

