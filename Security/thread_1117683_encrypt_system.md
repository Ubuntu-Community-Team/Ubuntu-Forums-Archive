---
title: "encrypt system"
date: 2009-04-06
forum: Security
---

### Post by geo75 on 2009-04-06
I am using ubuntu 8.10 on my laptop, but system is not encrypted. 
can I encrypt the drive or can I ONLY do that during the initial install? I do not want to reinstall...
I've downloaded truecrypt, but it does not seem to have system encryption option for linux :(

---

### Post by bodhi.zazen on 2009-04-06
You have to re-install to encrypt the system (well, you do not *have* to, but it is easier).

You can not use truecrypt ot encrypt the system, use LUKS.

You *could* mane a LUKS crypt and manually move and configure your system if you wish, but it would all be manual changes to the system and take more time then installing from the alternate CD.

The alternate is to use truecrypt, ecryptfs, or encryptfs to encrytp your user files / data.

---

