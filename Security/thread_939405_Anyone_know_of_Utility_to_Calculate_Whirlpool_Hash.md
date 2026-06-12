---
title: "Anyone know of Utility to Calculate Whirlpool Hash Digests?"
date: 2008-10-05
forum: Security
---

### Post by kevdog on 2008-10-05
I'm looking for a utility to calculate Whirlpool Hashes.  Openssl has only included this hash in the developmental version (no stable versions thus far).  Is there any other utility that may do this calculation?

---

### Post by kevdog on 2008-10-06
By the number of responses, it doesn't seem like most people are interested in this ability, however I did find a package called md5deep.  Despite its name its capable of producing md5, sha1, tiger192, sha256, and whirlpool hashes.  It can do this recursively, store the output, and later compare the stored output to another recursive scan to let someone know what has changed in the scanned directory tree:  [http://md5deep.sourceforge.net/](http://md5deep.sourceforge.net/)

It is available via the apt system:

sudo apt-get install md5deep
sudo aptitude install md5deep

Of course it can also be easily compiled and installed from source.  

Hopefully someone else my find this useful.

---

### Post by Dr Small on 2008-10-06
I think this fellow has found a utility that does just that:
[http://ubuntuforums.org/showthread.php?t=939545](http://ubuntuforums.org/showthread.php?t=939545) ;)

---

