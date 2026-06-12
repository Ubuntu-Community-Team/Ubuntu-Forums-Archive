---
title: "How can I upgrade to GPG 1.4.10"
date: 2010-03-05
forum: Security
---

### Post by donsy on 2010-03-05
In Synaptic the highest release is 1.4.9.

---

### Post by ratcheer on 2010-03-05
You can get the latest source code and compile and install it:

[http://www.gnupg.org/download/index.en.html](http://www.gnupg.org/download/index.en.html)

Tim

---

### Post by ptn107 on 2010-03-06
Try using the version from Debian's repositories:

_[gnupg 1.4.10 32-bit]("http://ftp.us.debian.org/debian/pool/main/g/gnupg/gnupg_1.4.10-2_i386.deb")_
_[gnupg 1.4.10 64-bit]("http://ftp.us.debian.org/debian/pool/main/g/gnupg/gnupg_1.4.10-2_amd64.deb")_

Then to install:
```
sudo dpkg -i gnupg_1.4.10-2_i386.deb
```
(or *gnupg_1.4.10-2_amd64.deb* for the 64-bit version.)

---

