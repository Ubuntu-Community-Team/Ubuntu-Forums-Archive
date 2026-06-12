---
title: "Rkhunter  public key ?"
date: 2015-01-07
forum: Security
---

### Post by cogset on 2015-01-07
I was going to install the latest (current) version of Rkhunter 1.4.2 from here [http://sourceforge.net/projects/rkhunter/files/rkhunter/1.4.2/](http://sourceforge.net/projects/rkhunter/files/rkhunter/1.4.2/) and discovered that there is an .asc signature file there, but then the public key with which verify said signature  is nowhere to be found: no keyserver that I know of has this key:
```
gpg --verify  rkhunter-1.4.2.tar.gz.asc   rkhunter-1.4.2.tar.gz
gpg: Signature made Thu 13 Mar 2014 07:52:42 AM CET using RSA key** ID 26447505**
``` and a quick search on the web returns no useful results either.
Does anyone know if such public key exists at all? What is one supposed to do in this case?

---

### Post by unspawn on 2015-01-07
As the documentation says: please consider checking the README, FAQ and the rkhunter-users mailing list archives. From the latter: 'gpg --keyserver subkeys.pgp.net --search 26447505', 'gpg --keyserver subkeys.pgp.net --search C2B0898226447505'.

---

### Post by cogset on 2015-01-07
Have you read my post? The key **26447505** is nowhere to be found on the keyservers I know, there is no reference at all to public keys in the README and FAQ, and the info in the rkhunter-users mailing list archives (pointing to this very key) dates back to 2008.

---

### Post by unspawn on 2015-01-08
Oh well search any of pgp.mit.edu, subkeys.pgp.net or hkps.pool.sks-keyservers.net for "0xea5f4cd3a65f5e17" then.

---

