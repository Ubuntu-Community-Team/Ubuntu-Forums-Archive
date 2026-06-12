---
title: "Full RW access for EXT2, EXT3, EXT4 file systems in Windows XP, Windows 7, Windows 8"
date: 2015-01-10
forum: Ubuntu, Linux and OS Chat
---

### Post by nathan60 on 2015-01-10
I wanted to offer some advice for those (like me) who still need full access to Linux EXT4 partitions.  "Paragon ExtFS for Windows" is the program I use, and it has worked great for me in Windows 7.  At the time of this post the program is still free and claims to work in Windows XP through Windows 8.1 as well as Windows Server 2003 and 2008, and I say they "claim" because I've only used it in Windows 7 x86 and 64bit so I only vouch for it's efficacy in those I've used.  Here is their download page:
[http://www.paragon-software.com/home/extfs-windows/](http://www.paragon-software.com/home/extfs-windows/)

I'd be happy to answer anyone's questions about it from my point of view as a user, but I am not a developer and still fairly new to Ubuntu!

Anyway, I hope this helps anyone who've been looking for full RW EXT2 / EXT3 / EXT4 mounting in Windows :)

---

### Post by mastablasta on 2015-01-12
though it might be still better (safer?) to have an NTFS DATA partition mounted in Linux and Windows.

but it's good to know tools exist and they might still come in handy for us dualbooters.

---

### Post by coffeecat on 2015-01-12
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by Holger_Gehrke on 2015-01-12
Interesting. Never heard of it before, probably because I've been using [http://www.ext2fsd.com](http://www.ext2fsd.com) (Open Source, GPL V2) for three or four years now ...

---

### Post by timonoj on 2015-02-24
> **Holger_Gehrke said:**
> Interesting. Never heard of it before, probably because I've been using [http://www.ext2fsd.com](http://www.ext2fsd.com) (Open Source, GPL V2) for three or four years now ...

How well does it work, though? 2 or 3 years ago the place where I saw it recommend it had stern warnings about it being dangerous and capable of corrupting your FS because it might handle permissions differently...

The thing is, I need to sync some seafile folders (think of dropbox), which are rather big (20GB, 40GB, etc). So I'd rather keep a single set of them in the computer instead of having to replicate them for each OS. I'd like to be able to access&sync them both from WIndows and Linux. So far, NTFS-3g seems to be handling the permissions not so very nicely, and leading to the folder being permanently detected as changed.

---

