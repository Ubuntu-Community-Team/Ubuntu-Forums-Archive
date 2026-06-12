---
title: "Encrypting a USB Stick Partition"
date: 2010-10-28
forum: Security
---

### Post by pteri498 on 2010-10-28
I'm trying to think of the best way to encrypt a partition on my flash drive.

I plan on storing ssh/pgp keys on it for use on different computers (including school computers, where I won't have administrative access).

TrueCrypt is going to require admin access to decrypt and mount the partition, I think, so that's out.

Are there any other methods you all would recommend?

Thanks.

---

### Post by HermanAB on 2010-10-29
Howdy,

You can try LUKS and FreeOTFE:
[http://www.aeronetworks.ca/luks-usb-howto.html](http://www.aeronetworks.ca/luks-usb-howto.html)

However, password protected Zip files are the easiest and universally supported.

---

