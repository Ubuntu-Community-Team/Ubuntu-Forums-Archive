---
title: "Truecrypt on Dual boot system"
date: 2008-10-24
forum: Security
---

### Post by CyberCowboy on 2008-10-24
Hello,

My father is looking for an encrypted dual boot system and I think truecrypt may be the answer.  My question is what is the easiest way to encrypt the whole disk, but allow dual boot?  My thought was as follows

Install Windows
Install Windows Version of TC and setup full disk encryption
Install Ubuntu

My only question is will installing Ubuntu over-write the TrueCrypt boot area that would allow the system do decrypt?

---

### Post by nubdora on 2008-10-24
I did some researching and I also saw your post on the Truecrypt forums. 

Of all that I have read, I understand it is not possible to do what you are wanting because Truecrpyt and other encryption software do not support it. Although some may claim it can be done, it can't. 

Encryption software is able to perform a full system encryption that will encrypt all partitions, but you will not be able to dual-boot from a single disk because, simply, the encryption bootloaders can not handle this request yet. You can create a "hidden operating system" and this setup is as close to full-encypted dual-booting as can be achieved at this point. 

Here is the rough "how-to":

[http://forums.truecrypt.org/viewtopic.php?t=11731](http://forums.truecrypt.org/viewtopic.php?t=11731)

Your "hidden operating system" should be the one you boot into the least *or* the system you are putting the most sensitive information on. You will still want to boot into the "decoy" system often so it appears to be the "decoy" system containing current dates, times, and file modifications if your reason for the "hidden operating system" is to store sensitive data. 

I tend to "" a lot. I sware I don't do it with my fingers irl when I'm talking though.

---

