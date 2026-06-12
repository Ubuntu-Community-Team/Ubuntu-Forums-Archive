---
title: "How do I use TrueCrypt with non-ext3 partitions?"
date: 2010-03-23
forum: Security
---

### Post by zozza on 2010-03-23
Hi, 

When you are creating a TrueCrypt partition it asks what filesystem you will be using:

None 
FAT
EXT2
EXT3

This is fine if you decide to create your partition on Linux but I am wondering what you would do if you wanted to create it on your XP partition and access it through the mounted drive.

My XP is NTFS and that option does not appear.

Thanks.

---

### Post by bodhi.zazen on 2010-03-23
From here :

> [B]Is it possible to change the file system of an encrypted volume?

[/B]       Yes, when mounted, TrueCrypt volumes can be formatted as FAT12,  FAT16,          FAT32, NTFS, or any other file system. TrueCrypt volumes behave  as standard          disk devices so you can **right-click the device icon (for example  in the '*Computer*' or '*My Computer*' list) and select '*Format*'.**  The actual volume contents will be lost. However, the whole volume will  remain encrypted. If you format a TrueCrypt-encrypted          partition when the TrueCrypt volume that the partition hosts is  not mounted,          then the volume will be destroyed, and the partition will not be  encrypted          anymore (it will be empty).


[http://www.truecrypt.org/faq](http://www.truecrypt.org/faq)


Personally the truecrypt web site is the best source of information on truecrypt.

---

### Post by zozza on 2010-03-25
Perhaps I did not explain myself very well - and I did look at the manual beforehand and could not see an answer.

I am not talking about existing volumes but creating a NEW volume.

There is no option to create it on an NTFS system.  If I am using Ubuntu but for some reason wish to create it in the XP system should I just create it as a FAT system since the option I want (NTFS) does not exist?

Thanks.

---

### Post by bodhi.zazen on 2010-03-25
> **zozza said:**
> Perhaps I did not explain myself very well - and I did look at the manual beforehand and could not see an answer.

I am not talking about existing volumes but creating a NEW volume.

There is no option to create it on an NTFS system.  If I am using Ubuntu but for some reason wish to create it in the XP system should I just create it as a FAT system since the option I want (NTFS) does not exist?

Thanks.

My guess is you first create a new volume, use FAT or ext2 or ext3.

then re-format it as NTFS.

It may well be a two step process for you.

Otherwise, as Truecrypt is a 3rd party application ask on their mailing list or forums.

---

### Post by adam814 on 2010-03-25
If you have Windows XP and you're concerned with interoperability with TrueCrypt volumes why not create it with TrueCrypt for Windows?  I'm certain it will create a new NTFS volume (eliminating the need to reformat it) and then TrueCrypt on Linux should still mount it fine.

---

