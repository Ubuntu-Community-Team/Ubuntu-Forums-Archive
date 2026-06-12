---
title: "Elegant and Simple PArtition encryption?"
date: 2009-12-05
forum: Security
---

### Post by paradigm2 on 2009-12-05
Hello all. I have Karmic (9.10) installed and am using the encrypted /home feature which I believe uses ecryptfs?  Anyway I would also like to encrypt two other partitions I have on separate disks. One a 20GB disk and the other a 80GB disk.  Does anyone have any suggestions on the most elegant and simple way to do this?

Ideally I would like to use the same mechanism which is used for encrypting my /home -- the same password and everything.  I would like to be able to just login and have it automatically decrypted and mounted.

Any tips, suggestions, or pointers to good documentation?  Thank you.

---

### Post by ahtokca on 2010-12-10
I'd use cryptsetup. Have you read that?

[http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/](http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/)

---

