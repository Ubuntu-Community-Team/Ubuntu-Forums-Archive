---
title: "Encrypt Existing Home Directories?"
date: 2010-06-05
forum: Security
---

### Post by klausner on 2010-06-05
Is there a way to encrypt existing home directories in lucid so that they will unlock with pam-encfs when the user logs in? Or must you do this when the directory is created?

---

### Post by HermanAB on 2010-06-05
yes, you can do it after the fact, but it is a bit tricky.  It is certainly easiest to configure encryption during the system installation.

Here is a guide that should give you some idea of what is involved:
[http://www.aeronetworks.ca/luks-usb-howto.html](http://www.aeronetworks.ca/luks-usb-howto.html)

---

