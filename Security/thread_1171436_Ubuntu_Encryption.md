---
title: "Ubuntu Encryption"
date: 2009-05-27
forum: Security
---

### Post by okayneil on 2009-05-27
One of the tools I always wanted to get working was the encryption system within Ubuntu, you know when you right click on a folder/file and select encrypt? Im a trainee Scenes of Crime Officer (C.S.I.) and will soon need to store work on my computer thats of a sensitive nature. 

So I did some research on how to get it up and running but from what Ive come across it seems the majority advise against it, they propose using other pieces of software. I always thought it was a service built into the ubuntu code but obviously not. 

For someone wishing to use encryption I was wondering what everyone would advise?

---

### Post by Cheesemill on 2009-05-27
I've never encrypted individual files/folders, I've just gone for full disk encryption.

It's easy to set it up during installation if you use the alternate install CD.

Cheesemill

---

### Post by tubbygweilo on 2009-05-27
okayneil, following on from Cheesemill I would recommend you make encrypted backups of your sensitive data using Truecrypt (insert something your choice) so that in the event of your machine failing or you forgetting your encryption passphrase your data would be safe and sound. You could even challenge your fellow CSI dudes to try their skill at cracking your fully encrypted machine;)

---

### Post by okayneil on 2009-05-27
> **tubbygweilo said:**
> okayneil, following on from Cheesemill I would recommend you make encrypted backups of your sensitive data using Truecrypt (insert something your choice) so that in the event of your machine failing or you forgetting your encryption passphrase your data would be safe and sound. You could even challenge your fellow CSI dudes to try their skill at cracking your fully encrypted machine;)

Having checked out Truecrypt i would use it once in a while to do exactly what it sats it does but i would also like something that would allow me to immediatley encrypt files. 

Any ideas?

---

### Post by HermanAB on 2009-05-27
GPG of course.

---

### Post by rileinc on 2009-05-28
The "Encrypt..." option in the right-click menu uses _[GPG](http://ubuntuforums.org/showthread.php?t=687173)_. It's handy for encrypting and verifying the integrity of sensitive data when transmitting over wire or wirelessly.

If you wish to use encryption to protect data on your laptop from unauthorized persons (in the event the laptop is lost or stolen), then look into _[full-disk encryption](http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04)_. This encrypts everything on the hard disk as files are created or copied onto it.

---

### Post by rookcifer on 2009-05-28
Whole disk encryption is the only way to go (and the most secure).  The link rileinc posted above shows all the steps of how to set it up on Ubuntu using the alternate CD.

---

### Post by okayneil on 2009-05-28
> **rookcifer said:**
> Whole disk encryption is the only way to go (and the most secure).  The link rileinc posted above shows all the steps of how to set it up on Ubuntu using the alternate CD.

Is a re-install really necessary or can it be done on a pre-existing install?

---

