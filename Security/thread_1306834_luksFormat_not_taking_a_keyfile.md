---
title: "luksFormat not taking a keyfile"
date: 2009-10-30
forum: Security
---

### Post by Deathcon_1 on 2009-10-30
I'm trying to setup luksFormat to take a key file for the hard drives using the folliwing command:
```
cryptsetup -c aes-cbc-essiv:256 -y -s 256 luksFormat /dev/sda file.key
``` only it fails with a strange error:
"Command faied: Can't do passphrase verification on non-tty inputs"

It works if I use a password but for obvious reasons I want to use a keyfile.  I've setup cryptsetup's before so this isn't my first time setting them up.  Any ideas?

---

