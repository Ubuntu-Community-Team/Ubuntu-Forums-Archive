---
title: "mount -t ecryptfs fails"
date: 2011-07-12
forum: Security
---

### Post by Mappenz on 2011-07-12
Hi,

i want to encrypt a single folder. I use a method i found multiple times on different sites:

```

michael@michi:~/Bilder$ sudo mount -t ecryptfs .nata12072011 nata12072011
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 8; min keysize = 4; max keysize = 56 (loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (loaded)
Selection [aes]: 
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 
Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: 
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=7f69041312d06e06
Error mounting eCryptfs: [-22] Invalid argument
Check your system logs; visit <http://launchpad.net/ecryptfs>

```

I don't understand the problem. In this case i just just pressed enter, exept for the passphrase. The passphrase is about 10 digits long. I get the same error even if i follow different instructions by the book.

---

