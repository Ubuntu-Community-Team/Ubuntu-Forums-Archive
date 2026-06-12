---
title: "What are the advantages/disadvantages of full Data Encryption?"
date: 2008-10-17
forum: Security
---

### Post by thenetduck on 2008-10-17
Hi

I want to be able to encrypt some data so that you need a pass code to access it. Does anyone know what the advantages/disadvantages of Full Disk Data Encryption is? Does it slow your machine down? Is it worth it? I have some important finical information I want kept safe. 

Thanks 
The Net duck

---

### Post by bodhi.zazen on 2008-10-17
The advantage is keeping data safe.

But your data is only safe when it is encrypted. Once it is decrypted it is the same as any other file or partition.

So, lets say you have an encrypted partition /dev/sd007

The data will not be readable until you mount it, and to mount it you will need a password.

Once you enter the password and mount the data it is decrypted and will act like any other partition.

Same goes for directories and files.

Holds true for any encryption algorithm.

There is obviously some "overhead" with encryption, but this will vary by technique (ie gpg vs truecrypt vs *encryptfs* vs LUKS). 

In practice I do not see much of a performance hit on a desktop running an encrypted root and swap partition.

=====

I think the better question is what do you want to accomplish with encryption ?

In a nut shell encryption protects you data if someone has physical access to your system or data and the file (or directory or file system) is unmounted.

Once the data is decrypted it is no more or less secure than any other data.

---

### Post by thenetduck on 2008-10-17
Can I just encrypt one folder?

---

### Post by Dave_Connor on 2008-10-17
Yeah with Encfs and fuse and it works well but with full disc or encrypted directory you want to always make an unencrypted backup in case you get screwed over.

---

### Post by Drezard on 2008-10-17
Yes, using PGP.

Daniel

---

### Post by jerome1232 on 2008-10-17
I've noticed when doing large file transfers between 2 encrypted partitions my transfer speed was knocked down noticeably. (a few megabytes/sec) My processor was bottlenecking the process though as it was at a full hundred precent, this is an amd64 3700+.

edit: really what's the point of encryption if your are going to make an unencrypted backup?

Maybe encrypt the backup with a different key...

---

### Post by hyper_ch on 2008-10-18
> **Dave_Connor said:**
> with full disc or encrypted directory you want to always make an unencrypted backup in case you get screwed over.

Nope, you can put it onto another encrypted device ;) However I agree with the backup... and no matter what, you should always have a backup, regardless of whether you use encryption, regardless of whether you're going to repartition a few things... having backups is a must because there can always be something that messes your data totally up (e.g. harddisk may fail).

---

### Post by pietjanjaap on 2008-10-18
If you do a full encryption, then if your harddrive gets damaged then it is possible that everything is gone, because you have 1 big file on the disk, this very unsafe.
But if you make with truecrypt on a disk like 5 file's, then if 1 file gets damaged, the other 4 you can get back.

---

### Post by hyper_ch on 2008-10-18
> **pietjanjaap said:**
> If you do a full encryption, then if your harddrive gets damaged then it is possible that everything is gone, because you have 1 big file on the disk, this very unsafe.
But if you make with truecrypt on a disk like 5 file's, then if 1 file gets damaged, the other 4 you can get back.

That's why you need backups ;)

---

