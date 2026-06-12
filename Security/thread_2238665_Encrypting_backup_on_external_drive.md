---
title: "Encrypting backup on external drive?"
date: 2014-08-09
forum: Security
---

### Post by cogset on 2014-08-09
I have several backups on an external hard disk,I was wondering if it is possible to encrypt them without first copying them somewhere else,then encrypt the whole device,and finally copying them back.
In other words,is there any way to encrypt those files "in place",so to speak?

I may have also two related questions:
-if this can be done at all,can it be done using only linux native tools instead of specific software?
-once you have an encrypted backup,will you still be able to use rsync to update it?

---

### Post by fyfe54 on 2014-08-09
I use the Deja-Dupe backup tool in Trusty.  It encrypts too.

---

### Post by cogset on 2014-08-10
That's not what I'm looking for:I already have my backups on a separate drive,I was after a way to (possibly) encrypt them in place,without all the exercise of  temporarily copying  on another support,encrypt the whole device and then transfer them back.

Besides,I need to have all the files normally accessible (once decrypted,of course) which  DejaDup doesn't allow,and I've more or less got the hung of rsync,therefore I'd like to continue using it.

In case the *temporary copy-encrypt the device-transfer the files back* is the only safe and viable option,I'd rather do that than risk losing the backups or use another backup method which I'm not familiar with.

---

