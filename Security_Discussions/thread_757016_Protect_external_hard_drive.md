---
title: "Protect external hard drive"
date: 2008-04-16
forum: Security Discussions
---

### Post by alphajean@gmail.com on 2008-04-16
Hi,
I have bought a new external 500Gb hard drive to keep important information for me there.
The question is how to protect this hard drive, I don't want to people can read this info from Linux or Windows system?

Any programs ?

---

### Post by alphajean@gmail.com on 2008-04-16
?

---

### Post by cdenley on 2008-04-16
[http://www.emcken.dk/weblog/archives/164-Encrypted-USB-drive-in-Ubuntu.html](http://www.emcken.dk/weblog/archives/164-Encrypted-USB-drive-in-Ubuntu.html)

---

### Post by luckyme2 on 2008-04-16
> **alphajean@gmail.com said:**
> Hi,
I have bought a new external 500Gb hard drive to keep important information for me there.
The question is how to protect this hard drive, I don't want to people can read this info from Linux or Windows system?

Any programs ?

Truecrypt !

Use it on the whole disk. works very good, but initializing might take some time.
But once over that hurdle it is protected as a charm.

Her's the link :

[http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php)

---

### Post by The Cog on 2008-04-16
You might want to look at encfs [http://ubuntuforums.org/showthread.php?t=148600](http://ubuntuforums.org/showthread.php?t=148600) which allows you to have an encrypted directory on an otherwise unencrypted disk. It's easy to set up.

---

### Post by PetePete on 2008-04-17
agree with The Cog,
if you are encrypting a whole drive  you dont wanna be using truecrypt , but rather use encfs or similiar encrpted file system

---

### Post by hyper_ch on 2008-04-18
if it should be available only in linux, then rather use luks/dm_crypt for encrypting the devices... if it shall be accessible by linux, windows, .... then use truecrypt

---

