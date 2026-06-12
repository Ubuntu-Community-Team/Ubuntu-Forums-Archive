---
title: "Virtual encryption fs"
date: 2015-01-26
forum: Ubuntu, Linux and OS Chat
---

### Post by greg66 on 2015-01-26
I'm looking for a software which would provide, in a folder, a virtual crypted version of a folder on my local drive. That is, the opposite of ecryptfs. My goal is to have a almost zero-sized folder which I can backup. Do you know such software?


Thanks in advance


greg

---

### Post by deadflowr on 2015-01-26
encfs?

---

### Post by greg66 on 2015-01-27
> **deadflowr said:**
> encfs?
Thanks for your answer. From what I understand ecryptfs and encfs (and most software) work the same way: the data is encrypted on disk and is accessed in clear. I want the opposite: the data is clear on disk and read encrypted.

---

### Post by kevdog on 2015-01-27
So its not really encrypted but if somebody reads the data it looks to be encrypted?  That's kind of silly.  So it's like psuedo-secure.  What do you mean read encrypted?  What would be reading it.  Encfs and ecryptfs only decrypts the folder when its mounted.  I guess when what-ever folder is mounted you'd like to encrypt it?  But that begs the case that when the folder is unmounted it would be able to be read. Why would you mount it then?

---

### Post by greg66 on 2015-01-27
> **kevdog said:**
> So its not really encrypted but if somebody reads the data it looks to be encrypted? 
Exactly. I want to keep the data clean physically on my disk, but I want to backup the data off-site encrypted.

---

### Post by deadflowr on 2015-01-27
> **greg66 said:**
> Exactly. I want to keep the data clean physically on my disk, but I want to backup the data off-site encrypted.

Isn't that what duplicity does?

---

### Post by greg66 on 2015-01-30
> **deadflowr said:**
> Isn't that what duplicity does?
It should be, but if I'm not mistaken it has two problems: it first creates local compressed/encrypted copies of files, and I couldn't make it work with hubic, the backup provider I want to use...

---

