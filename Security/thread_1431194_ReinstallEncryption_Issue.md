---
title: "Reinstall/Encryption Issue"
date: 2010-03-16
forum: Security
---

### Post by uRock on 2010-03-16
I had to install Karmic over Lucid due to some issues I was having with it and now when I try to install Karmic I cannot get it to mount the encrypted home. Neither the LiveCD nor the alternate installer ask me for the encryption key anywhere during the install process, what do I have to do?

Thanx,
Ronnie

---

### Post by uRock on 2010-03-16
I am wondering if there is an easy command that could be run from the LiveCD. Karmic boots, but cannot mount the /home. It doesn't ask for the key either.

---

### Post by uRock on 2010-03-16
Never mind. Formatted partition. I am upset that I can't have an encrypted hard drive on an easily stolen Netbook. I tried reinstalling with both the Alternate installer and the LiveCD and neither offer a way to access the already encrypted partitions.

---

### Post by bodhi.zazen on 2010-03-16
> **iRock said:**
> Never mind. Formatted partition. I am upset that I can't have an encrypted hard drive on an easily stolen Netbook. I tried reinstalling with both the Alternate installer and the LiveCD and neither offer a way to access the already encrypted partitions.

I hear your frustration, but, what were you expecting ? That is the whole point of encryption. Encryption makes it one step more complex ...

The answer to your question depends on which tool you used to perform the encryption - LUKS or ecryptfs.

[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)

LUKS is a bit easier, in general see:

[How to: Resize an Encrypted Partition (LUKS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=4530641")

For any type of shared partition I prefer LUKS

---

### Post by uRock on 2010-03-16
It was encryptfs. Thank you for helping me out. I am probably going to make an encrypted folder. I'll wait and do an encrypted install again when I install Lucid next month.

---

