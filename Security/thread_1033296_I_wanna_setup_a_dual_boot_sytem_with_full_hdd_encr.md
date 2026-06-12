---
title: "I wanna setup a dual boot sytem with full hdd encryption"
date: 2009-01-07
forum: Security
---

### Post by LexLuthor08 on 2009-01-07
ok I am really a noob with this. The only thing I did so far was follong this tutorial step for step on my laptop: [http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/](http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/) .

Now, I'd like to do something more complicated: a dual boot system with vista and ubuntu. I'd like to stick with dm-crypt of the alternative cd as much as possible.

The final result should be like this: When I start up, it asks for a passphrase. Vista is a "plausible deniability OS" which will start with one password. But no one knows that there is a second password, which will boot ubuntu. :D
how can I do that?

---

### Post by Tubes6al4v on 2009-01-08
I have been attempting to do a hidden linux OS as well, but as far as I have seen, this cannot be done yet with the standard tools (Luks, dm-crypt, trucrypt,etc). Even if you were able to boot vista through Luks,someone could just see an ecrypted partiton and work to get you to release the key for it.

I assume you have taken a look at Truecrypt ( [www.truecrypt.com](www.truecrypt.com) ) and have seen that you can hide windows in an hidden volume of an encrypted container. I suggest you read their description of all of it to understand the purpose. You might be able to use the Truecrypt boot loader to boot into Ubuntu, which will then ask you to decrypt that partition. However, atm, Truecrypt does not support hidden OS's on Linux or Mac.

---

### Post by flatline on 2009-01-08
I came in here looking for this same thing, except I don't really want vista on my computer.  Just the full-disk pre-boot encryption, although plausible deniability is a plus.  My company has McAfee Safeboot on all of the computers, and I like it more than the "file containers" available for Linux in TrueCrypt and BestCrypt.

I guess for now I will stick with TrueCrypt thanks to the OS X compatibility.

---

### Post by hyper_ch on 2009-01-09
what do you mean with full-disk pre-boot encryption?

---

### Post by Tubes6al4v on 2009-01-09
I think he is refering to pre-boot authentication. Wikipedia has a reference to it on its "comparison of disk ecryption software" page. 

[http://en.wikipedia.org/wiki/Comparison_of_disk_encryption_software](http://en.wikipedia.org/wiki/Comparison_of_disk_encryption_software)

I am not sure how this works though. I guess it would just be a front end for decrypting everything else (isn't this just about the same as having to leave /boot decrypted?) On that note, do hardware encrypted hard drives have something like this? I thought that they had everything encrypted.

---

### Post by flatline on 2009-01-09
Yes, I meant full-disk encryption with pre-boot authentication.  That is, the entire hard drive with the exception of the crypto system is encrypted.  The bootloader cannot execute without an authorized password.  

One advantage to this approach is that it is then more or less transparent to the OS below.  As far as I can tell, once I have decrypted my work laptop, Windows doesn't even know it was ever encrypted.  This is mainly useful if your laptop is stolen.  The password is not stored anywhere on the system - it is verified by using it to decrypt a portion of the boot code.

I have decided to take a more traditional approach however and stick with TrueCrypt to allow my USB drives to work across my Linux and OS X machines.

---

