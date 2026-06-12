---
title: "Encryption of an external hard drive used also with Windows or Max OS"
date: 2016-05-29
forum: Security
---

### Post by Mamoth on 2016-05-29
Hi.

My search in the forums on this topic has returned nothing so I start this thread.

I have an external USB hard drive which I use with my laptops (running Ubuntu or Linux Mint) but also with other computers running Windows. I might have in the future to use it with Macs.
It is currently NTFS formatted although reformatting it would not be an issue.

I wish to protect its content by encrypting it. A few years ago I would simply have used TrueCrypt but since it is not supported any longer, I am wondering if I'd better not search for another solution.
Creating a LUKS partition would not not work with Windows OS. Similarly using BitLocker would not work with Linux.

Any idea ?

---

### Post by atl45 on 2016-05-29
VeraCrypt is free and opensource encryption software.  You could encrypt the drive with VeraCrypt, create a VeraCrypt file container on the drive, or create a Veracrypt partition on the drive. VeraCrypt works just fine in Linux and is what I use for everything other than FDE of my Ubuntu system partition (VeraCrypt can't do FDE of Linux partitions so for this I use LUKS). VeraCrypt can also convert TrueCrypt volumes to VeraCrypt volumes if you still have any of those lying around. You'll want to reformat the drive from NTFS to FAT32 (see the VeraCrypt documentation for reasons why). You could encrypt it as an NTFS partition but its not recommended.  You should make yourself familiar with the VeraCrypt documentation before proceeding. Any final decision should be based on your own threat model.  Without wishing to start a discussion with others on the matter, BitLocker is proprietary software produced by Microsoft. Need I say more? This is why I also use VeraCrypt for FDE of Windows systems/partitions. There are other advantages of using VeraCrypt with Windows systems which are covered in the documentation.  Edit: There are several alternatives outlined in the following recent post, FYI: [http://ubuntuforums.org/showthread.php?t=2320019](http://ubuntuforums.org/showthread.php?t=2320019)

---

