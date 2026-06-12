---
title: "Idea?"
date: 2010-08-04
forum: Security
---

### Post by diablo69er on 2010-08-04
So I was curious, i've used srm and it's beyond over kill for what i Need it to wipe.

So I got to thinking and I came up with the following scenario.

What if my entire disc drive was encrypted, I created a Windows 7 VM, encrypted that as well, installed a software erase software on it, mved all my files that I need deleted to that encrypted windows vm and did about 16 passes on the data.  How hard was this be for someone to recover?

---

### Post by cdenley on 2010-08-04
If the file was always stored on the encrypted filesystem, then it can't be recovered unless they can decrypt the filesystem. If you move the file from your root filesystem to an encrypted disk image for a virtual machine, that does nothing to hide the original file except delete it. Creating another copy in the disk image, regardless of how many times it is encrypted or erased, would only be counterproductive.

---

### Post by bodhi.zazen on 2010-08-04
> **diablo69er said:**
> So I was curious, i've used srm and it's beyond over kill for what i Need it to wipe.

So I got to thinking and I came up with the following scenario.

What if my entire disc drive was encrypted, I created a Windows 7 VM, encrypted that as well, installed a software erase software on it, mved all my files that I need deleted to that encrypted windows vm and did about 16 passes on the data.  How hard was this be for someone to recover?

You are asking about the gutmann theory, which has been debunked.

One pass is sufficient

[http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)

cdenley already commented on the encryption.

---

### Post by Agent ME on 2010-08-05
> **diablo69er said:**
> What if my entire disc drive was encrypted, I created a Windows 7 VM, encrypted that as well, installed a software erase software on it, mved all my files that I need deleted to that encrypted windows vm and did about 16 passes on the data.  How hard was this be for someone to recover?
You can't "move" files to a different filesystem, such as the one on the VM. All you can do is make a copy onto the VM and delete the original. Except if you're trying to make data unrecoverable, making a copy is stupid, and the deleted original one is probably recoverable. Why not just use srm or shred with an option set to only do one pass?

---

### Post by diablo69er on 2010-08-06
Thanks for the questions everyone, it really helped me to understand things a bit better.

---

