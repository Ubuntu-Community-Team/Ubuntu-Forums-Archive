---
title: "encrypted filesystems"
date: 2010-06-05
forum: Security
---

### Post by discord on 2010-06-05
I'm just wondering what type of encryption ubuntu is using now to encrypt disks, and if there is some performance, benchmark information on the overhead used by such a system. I realize there is some information about this already out there, but the Ubuntu documentation page has not been updated in a  year and half. If anyone could comment and or point me to relevant sources, I'd appreciate it.

Thanks!

---

### Post by HermanAB on 2010-06-05
LUKS uses AES256 CBC ESSIV SHA256 by default.

The overhead is about 3% - quite negligible. So you have no excuse not to encrypt your home directory.

---

### Post by Agent ME on 2010-06-05
Just a nitpick: LUKS isn't used by the ubuntu installer for home directory encryption. That's EcryptFS. LUKS is for whole filesystem encryption. Not sure what the overhead of EcryptFS is.

---

