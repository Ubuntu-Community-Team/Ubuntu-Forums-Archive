---
title: "In place whole disk encryption"
date: 2009-03-23
forum: Security
---

### Post by jeyros12 on 2009-03-23
Hi there!
I've already installed the last desktop x64 Ubuntu. I'd now like to encrypt my system without having to install it again (it means I'd like to proceed to in place whole disk encryption).

Is there a way to do this?

Thanks

---

### Post by bodhi.zazen on 2009-03-23
No, if you wish the entire system to be encrypted you will have to re-install.

Alternates are to use truecrypt, ecryptfs, and LUKS to encrypt only your sensative data.

ecryptfs is a simple solution (and will likely be my next how-to).

for now :

```
sudo apt-get intstall ecryptfs-utils
```

Then :

```
ecryptfs-setup-private
```

This will set up a directory in your home, called "Private". The contents will be encrypted to .Private when you log out.

The contents are encrypted / decrypted automatically when you log on / off.

See also : [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

---

