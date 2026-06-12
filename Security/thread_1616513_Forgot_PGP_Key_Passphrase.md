---
title: "Forgot PGP Key Passphrase"
date: 2010-11-08
forum: Security
---

### Post by afrodeity on 2010-11-08
I think I accidently deleted my password phrase file in my home directory and now I can't unlock my SSH private key, either that, or I can't remember my password, and don't think i issue a revoke cert, would I have been prompted to issue one? How to revoke and generate new key?

```
cd  ~/.gnupg
private-keys-v1.d  random_seed  trustdb.gpg
gpg.conf                          pubring.gpg        secring.gpg

```

nothing which looks like a passphrase file?

---

### Post by afrodeity on 2010-11-08
bzr is asking me for access to an old key, is there a way to make it use a new key which I have password for?

---

### Post by alphaamanitin on 2010-11-09
If you didn't do a secure delete you can try to recover the file with file recovery software.  

AlphaA

---

### Post by afrodeity on 2010-11-12
file recovery software for linux is really bad, most utilities are file-carvers which carve up data further compounding problems. All i need is a simple recovery tool that checks for recent deletes, although I must admit chances of recovering the file in question are slim, i deleted it just before upgrading to maverick so you can imagine the amount of data that has shifted around on my hdd.

---

### Post by alphaamanitin on 2010-11-13
I have used TestDisk to recover things, but it might be way too much for what you want to use.

AlphaA

---

