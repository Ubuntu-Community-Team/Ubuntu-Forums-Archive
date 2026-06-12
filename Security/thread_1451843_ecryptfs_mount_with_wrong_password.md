---
title: "ecryptfs mount with wrong password?"
date: 2010-04-11
forum: Security
---

### Post by cd-r80 on 2010-04-11
Hi! I have .Private from 8.10. I can mount it: sudo mount -t ecryptfs .Private Private. But it never decrypts the files? It does not say nothing about the wrong password. It just asks: 

Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not 

etc. I suppose that it just makes a new crypted folder. Nothing todo with mounting old crypted files? I have only .Private backup & password. What I can really do? Well thank god I found also backup of old Private. But this just does not work if it is not possible move crypted files from other machine.

---

### Post by Agent ME on 2010-04-11
Do you have the mount password, or just your user password? The mount password is what you need. It's stored in ~/.ecryptfs, and is usually encrypted by your user password.

---

### Post by cd-r80 on 2010-04-12
What is this then?:

[http://packages.ubuntu.com/fi/karmic/ecryptfs-utils:](http://packages.ubuntu.com/fi/karmic/ecryptfs-utils:)
eCryptfs stores cryptographic metadata in the header of each file written, so that encrypted files can be copied between hosts; the file will be decryptable with the proper key, and there is no need to keep track of any additional information aside from what is already in the encrypted file itself.

I have used same password : user / encrypt. I think so...

---

