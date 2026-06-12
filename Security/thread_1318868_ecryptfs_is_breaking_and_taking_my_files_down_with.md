---
title: "ecryptfs is breaking and taking my files down with it"
date: 2009-11-07
forum: Security
---

### Post by Xitron on 2009-11-07
I have an ecryptfs folder in my home folder that I use to store things I don't want anyone to be able to access.  Suddenly, when I mount this folder, I'm getting the following sorts of errors...

001.txt.gpg:            writable, executable, regular file, no read permission
002.txt.gpg:            writable, executable, regular file, no read permission
003.txt.gpg:            GPG encrypted data
004.txt.gpg:            GPG encrypted data
005.txt.gpg:            GPG encrypted data
006.txt.gpg:            writable, executable, regular file, no read permission

I'm pretty sure that when I did the Karmic install (non-upgrade) I chose to let it encrypt my home folder, and now I'm starting to wonder if this encryption within encryption is causing this issue.  This data is pretty critical to me, and I'm a little afraid that I'm about to lose it all, as the list of bad files grows longer each time I run "file *".

Anyone else having similar ecryptfs problems?

---

### Post by bodhi.zazen on 2009-11-08
> **Xitron said:**
> I have an ecryptfs folder in my home folder that I use to store things I don't want anyone to be able to access.  Suddenly, when I mount this folder, I'm getting the following sorts of errors...

001.txt.gpg:            writable, executable, regular file, no read permission
002.txt.gpg:            writable, executable, regular file, no read permission
003.txt.gpg:            GPG encrypted data
004.txt.gpg:            GPG encrypted data
005.txt.gpg:            GPG encrypted data
006.txt.gpg:            writable, executable, regular file, no read permission

I'm pretty sure that when I did the Karmic install (non-upgrade) I chose to let it encrypt my home folder, and now I'm starting to wonder if this encryption within encryption is causing this issue.  This data is pretty critical to me, and I'm a little afraid that I'm about to lose it all, as the list of bad files grows longer each time I run "file *".

Anyone else having similar ecryptfs problems?

Backups are critical, more so for encrypted data as small problems with the encryption algorithms can mean you will not be able to access your data.

You can see if this link helps at all :

[http://bodhizazen.net/Tutorials/Ecryptfs](http://bodhizazen.net/Tutorials/Ecryptfs)

Otherwise it is hard to tell if those are warnings are actual problems.

Can you post the actual output you are getting ?

---

### Post by Xitron on 2009-11-08
I took the entire ecryptfs filesystem and moved it to a new area of the hard drive which is not encrypted like I think my home folder is, and all files work fine.  Best guess is that it was a case of an encrypted file (gpg) sitting in an encrypted folder (ecryptfs) which itself sits in an encrypted folder (ecryptfs).  I'll not repeat that mistake.  Thank you for your reply!

Unca Xitron

---

