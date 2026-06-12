---
title: "truecrypt encrypt ubuntu root partition"
date: 2008-02-12
forum: Security Discussions
---

### Post by trainpic on 2008-02-12
I would like to use truecrypt to encrypt the root volume on an Ubuntu laptop, but all the howtos are for chainloading an unencrypted Ubuntu partition from an encrypted windows partition. Can truecrypt boot encrypted Ubuntu root partitions? If so, how do I go about this?

---

### Post by AusIV4 on 2008-02-12
Considering TrueCrypt 5.0 won't even run until X is running, and they're no longer distributing 4.3a, this pretty much can't be done at the moment.

I'd recommend taking a look at LUKS and dm_crypt. TrueCrypt is awesome for file-based volumes that you can use on multiple platforms, but for full disk encryption, LUKS is the way to go. Plus, if you're not trying to convert an existing installation, you can do an encrypted system from the alternate CD.

---

