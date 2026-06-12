---
title: "Ubuntu 12.10 full disk encryption question"
date: 2012-10-27
forum: Security
---

### Post by soundsfromsound on 2012-10-27
Hello.

I was wondering what information is available on the type of encryption Ubuntu offers when using its new full-disk encryption.  Is it similar to TrueCrypt?  Is there any information about the algorithms, hashes, etc at all?  I've tried to Google the answer but nothing really comes up other than the fact that full encryption is possible. How strong is the Ubuntu 12.10 encryption?

Thank you for any feedback.

Sfs

---

### Post by Linuxisfast on 2012-10-27
It is similar to TC except it uses LUKS system, I do all my laptops this way.

---

### Post by soundsfromsound on 2012-10-27
Ah, gotcha.  Thank you for the fast and helpful response!  Much appreciated friend.

Sfs

> **Linuxisfast said:**
> It is similar to TC except it uses LUKS system, I do all my laptops this way.

---

### Post by soundsfromsound on 2012-10-27
One more thing: I read up on LUKS just now and am curious: is it 256 bit keys (AES) for Ubuntu 12.10?
(default key size)
I prefer 256 AES whenever possible, just curious - thanks!

Sfs

---

### Post by Linuxisfast on 2012-10-27
> **soundsfromsound said:**
> One more thing: I read up on LUKS just now and am curious: is it 256 bit keys (AES) for Ubuntu 12.10?
(default key size)
I prefer 256 AES whenever possible, just curious - thanks!

Sfs

Its 256-bit AES encryption in cipher-block-chaining mode.

---

### Post by soundsfromsound on 2012-10-27
Wonderful, thank you again!

> **Linuxisfast said:**
> Its 256-bit AES encryption in cipher-block-chaining mode.

---

### Post by soundsfromsound on 2012-10-27
Can I ask you one last question please?

So, if I encrypt my entire Linux laptop using the default Ubuntu 12.10 method, can't someone just bypass this entirely by using a LiveCD?  You know how you can easily bypass any Windows machine using a LiveCD and retrieve files that way?

How does a LiveCD work against full disk encryption?  Is there any true way to block the use of a LiveCD being able to read/access files on a machine?

Thank you so much for helping me with this.

Sfs

> **Linuxisfast said:**
> Its 256-bit AES encryption in cipher-block-chaining mode.

---

### Post by rookcifer on 2012-10-27
> **soundsfromsound said:**
> Can I ask you one last question please?

So, if I encrypt my entire Linux laptop using the default Ubuntu 12.10 method, can't someone just bypass this entirely by using a LiveCD?  You know how you can easily bypass any Windows machine using a LiveCD and retrieve files that way?

How does a LiveCD work against full disk encryption?  Is there any true way to block the use of a LiveCD being able to read/access files on a machine?

Thank you so much for helping me with this.

Sfs

A LiveCD wont help anyone read the data on the encrypted drive.  The only thing they could do would be to destroy your data, but reading it is out of the question unless they have the crypto key.

---

### Post by soundsfromsound on 2012-10-27
Oh, that's great to hear.  I thought you could bypass any OS (pretty much every "normal" machine) with a Linux LiveCD and at least access/retrieve files.  Nice to hear encryption will do the trick and prevent LiveCD-ness, thanks!

---

### Post by giowck on 2012-10-27
> **soundsfromsound said:**
> Oh, that's great to hear.  I thought you could bypass any OS (pretty much every "normal" machine) with a Linux LiveCD and at least access/retrieve files.  Nice to hear encryption will do the trick and prevent LiveCD-ness, thanks!

You can do this as long as data is not encrypted.

That's why encryption comes in!

---

### Post by soundsfromsound on 2012-10-27
Gotcha, thanks all! These forums are full of awesome helpful people!

Sfs

---

### Post by Linuxisfast on 2012-11-06
Thats why during install there is implicit warning that if you loose the key, you are finished with that install. Its impossible to crack it even using brute force method.

---

