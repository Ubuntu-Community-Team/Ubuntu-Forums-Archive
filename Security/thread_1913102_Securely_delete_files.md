---
title: "Securely delete files"
date: 2012-01-21
forum: Security
---

### Post by DrBob89 on 2012-01-21
Ubuntu 11.04

Shred does not appear to be available anymore and secure-delete man site ([www.thc.org](www.thc.org)) appears to be a hacker site that doesn't mention secure-delete.  Anybody have any other suggestions?

Buck

---

### Post by Ms. Daisy on 2012-01-22
You want to delete a file and then write zeros on the space where the files used to be? 

Try zerofree in the software center.

---

### Post by HermanAB on 2012-01-22
Shred and the like don't quite work, for various reasons.

If you want to have proper security, encrypt your file system.

---

### Post by sudodus on 2012-01-22
I think shred can still work in order to wipe a partition or whole drive. Probably it is possible for the intelligence services of the superpower states to recover the information from faint magnetic traces, if shred was set to overwrite several times, but I would say it is safely wiped. Maybe the default setting is too low.

But it is not reliable for files due to journaling and various automatic backup schemes. There might be other instances of the file that you shredded, and you cannot be sure that you find all of them.

And in a larger scale: when something is uploaded to the internet, it will stay there forever ...

Zerofree wipes/fills the unallocated 'nonzero' space with zeros, so that deleted files cannot be recovered with tools like PhotoRec, which is good against intruders, but bad if ***you*** need to recover deleted files. Unfortunately, zerofree cannot solve the problem of other instances of your deleted files, that you cannot be sure that you find.

---

### Post by jramshu on 2012-01-22
Try bleachbit.

---

### Post by gsgleason on 2012-01-25
What if you overwrite the file(s) with zeros/random data before deleting them?

---

### Post by sudodus on 2012-01-25
> **gsgleason said:**
> What if you overwrite the file(s) with zeros/random data before deleting them?
This is what is (was) done by shred. But as stated in the previous posts it is not enough on the file level. But it works when you want to wipe a whole disk drive.

I agree with *HermanAB*, that if you want to have proper security, encrypt your file system!

---

### Post by HermanAB on 2012-01-26
When your file system is encrypted, then to delete the files securely, you simply hit yourself upside the head with a brick to forget the password...

---

