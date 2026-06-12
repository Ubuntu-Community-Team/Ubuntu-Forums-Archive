---
title: "How to make it more secure"
date: 2012-04-28
forum: Security
---

### Post by loseby on 2012-04-28
Just installed 12.04 and then plugged in an external hard drive that 11.10 on it and copied my files across to this computer. Just thinking about it, that means anyone who gets this hard drive can just access the files from another Ubuntu installation  . Is this correct ?  How can I make this computer ( harddrive ) more secure ?


Basically new to Ubuntu and use it for all my banking / financial transactions but like what I see in this version and will start learning more about it ( starting here ) . 

Also is it a good idea to have an AV program ? 

btw: I do have a very strong password to logon

---

### Post by christhisisgool on 2012-04-28
As for the thing about the antivirus, to put it simply, no. The only reason that you would need an antivirus on ubuntu is if you are going to be sending files back and forth between windows boxes and you want to keep them safe. 
And, for the hard drive issue, simply encrypt it. there are various ways to do this, as well as to encrypt your home folder. to do either of these things, go to here: [https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorage](https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorage)
i have used that page to do all of my encryptions, as it has a gui option using the disk-utility, so it isnt that hard. hope this helps!

---

### Post by Ms. Daisy on 2012-04-30
A good place to start is the [basic security wiki]("https://wiki.ubuntu.com/BasicSecurity").  Also see the [stickies ]("http://ubuntuforums.org/showthread.php?t=510812")in the security forum.

For banking/financial transactions on the internet, I encourage you to pay attention in particular to  browser security.

---

### Post by CharlesA on 2012-04-30
> **losbey said:**
> Just installed 12.04 and then plugged in an external hard drive that 11.10 on it and copied my files across to this computer. Just thinking about it, that means anyone who gets this hard drive can just access the files from another Ubuntu installation  . Is this correct ?  How can I make this computer ( harddrive ) more secure ?

Remember that physical access = root access. If you encrypt the drive, anyone who doesn't know the encryption passphrase will not be able to access the drive.

Of course, if you forget the passphrase yourself, you are pretty much out of luck.


> Basically new to Ubuntu and use it for all my banking / financial transactions but like what I see in this version and will start learning more about it ( starting here ) . 

The browser would be more important than the OS itself - check the links that Ms. Daisy posted.

> Also is it a good idea to have an AV program ?

You would only need one if you are sharing files between Windows and *nix.

> **Ms. Daisy said:**
> A good place to start is the [basic security wiki]("https://wiki.ubuntu.com/BasicSecurity").  Also see the [stickies ]("http://ubuntuforums.org/showthread.php?t=510812")in the security forum.

For banking/financial transactions on the internet, I encourage you to pay attention in particular to  browser security.

What she said.

---

