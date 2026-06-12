---
title: "encrypting important files"
date: 2008-02-09
forum: Server Platforms
---

### Post by thefatmoop on 2008-02-09
So i have network information, backups of lists of usernames/passwords and i need to carry them on my laptop at all times. Well i'm obviously worried of the worst case scenario. Is there a program that can encrypt files (under 5 meg) and use very strong encryptions? it doesn't need to be automated or anything of the such

---

### Post by faulkes on 2008-02-09
Trucrypt for linux.

[http://www.trucrypt.org](http://www.trucrypt.org)

While it doesn't specifically do files, you can create a virtual FS (file), store your required files, data on there.  Any time you need them, you can mount the FS and access the files as needed.

Faulkes

---

### Post by thefatmoop on 2008-02-09
PERFECT! thankyou this is better than what i was looking for

---

### Post by HermanAB on 2008-02-09
Note that encryption needs to consider the whole system.  To read an encrypted file, you need to decrypt it.  So if you are using a disk drive, then you end up with a plain text copy on the drive, which, even if you delete it, is still there.  

Some programs can also store temporary copies of files in /tmp, /var/tmp or /usr/tmp.  Sometimes a program can get swapped out and the file ends up in /swap, or you suspend the PC and the whole contents of RAM gets written to /swap or to a suspend file on the HDD.  You should now begin to see the problem.

Consequently, the only solution is to encrypt all vulnerable drives, including /home, /tmp and /swap and map /usr/tmp and /var/tmp to /tmp.  

The Linux standard encryption system is dm-crypt.

Cheers,

Herman

---

