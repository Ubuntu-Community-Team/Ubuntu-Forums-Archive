---
title: "Passphrase recover"
date: 2011-02-27
forum: Security
---

### Post by Miss. Dobson on 2011-02-27
Hello everyone,

I have come a long way with ubuntu in the past few days.  I wasn't even able to boot into my user account for some reason.  But was able to fix it to get back in :KS

Sadly I'm still not in the clear.  There was a file of great importance I put on Ubuntu that I cannot find.  I believe it was encrypted. (I choose the option to encrypt my home folder)  I made a file with my pass phrase but I guess it got encrypted along with everything else.  

Is there any way to recover this or change it?

---

### Post by uRock on 2011-03-01
Bump for move to Security Discussions.

Can you log into your account?

If yes, then open a terminal and run this command to get your passphrase. ```
ecryptfs-unwrap-passphrase
```

---

### Post by Sef on 2011-03-01
Read [Encrypted Private Directory]("https://help.ubuntu.com/community/EncryptedPrivateDirectory") in Ubuntu Documents.

If you need help in understanding, what the wiki is asking you to do, then please post where you have problems understanding.

---

