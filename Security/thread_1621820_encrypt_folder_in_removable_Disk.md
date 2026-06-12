---
title: "encrypt folder in removable Disk"
date: 2010-11-14
forum: Security
---

### Post by nicolasdiogo on 2010-11-14
hi folks,

i would like to encrypt a folder in a removable hard-disk.
i have looked at the ecryptfs but it seems to work only in the home partition.

would you guys have another option?

thanks,

Nicolas

---

### Post by nicolasdiogo on 2010-11-15
just bumping it..

i have found that i can encrypt the whole hard-disk using cryptsetup but i would rather encrypt single folders with different passwords.

any suggestions?


thanks,

---

### Post by DavePlummer on 2010-11-15
I use encfs and cryptkeeper. Both are in the repositories.

---

### Post by Enigmapond on 2010-11-15
> **nicolasdiogo said:**
> just bumping it..

i have found that i can encrypt the whole hard-disk using cryptsetup but i would rather encrypt single folders with different passwords.

any suggestions?


thanks,

I use TrueCrypt...for many years and it works just wonderfully.
[http://www.truecrypt.org/](http://www.truecrypt.org/)

---

### Post by nicolasdiogo on 2010-11-22
thanks,

but interesting enough TrueCrypt is not available in the ubuntu repos. 

any reason in particular?  i understand that it is possible to download it from their website - what is the reason?


with regards,

Nicolas

---

### Post by surfer on 2010-11-22
i use both, encfs (with cryptkeeper) and dm-crypt (cryptsetup).

encfs will encrypt everything at file level (i.e. the number of files and directories and the size is still visible), dm-crypt will encrypt your whole file-system. ubuntu will recognize dm-crypt encrypted volumes and give you a nice password prompt, when you insert the removable media.

---

### Post by HermanAB on 2010-11-22
Truecrypt is gratis, but it is not Free.

---

### Post by FuturePilot on 2010-11-22
> **nicolasdiogo said:**
> thanks,

but interesting enough TrueCrypt is not available in the ubuntu repos. 

any reason in particular?  i understand that it is possible to download it from their website - what is the reason?


with regards,

Nicolas

It has license issues. [http://www.mail-archive.com/distributions@lists.freedesktop.org/msg00274.html]("http://www.mail-archive.com/distributions@lists.freedesktop.org/msg00274.html")

---

### Post by magnatron on 2010-11-23
ecryptfs encrypts more than just the home partition it can encrypt on any slice. If you want extra double paranoid security after you setup your ecryptfs folder and have it mounted you can then encrypt the contents of the encrypted directory with GPG. :popcorn:

---

