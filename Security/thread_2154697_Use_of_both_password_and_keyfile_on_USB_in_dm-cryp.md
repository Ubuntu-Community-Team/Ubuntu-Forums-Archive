---
title: "Use of both password and keyfile on USB in dm-crypt,LUKS"
date: 2013-06-15
forum: Security
---

### Post by hotriado on 2013-06-15
Is it possible to use both a password and a keyfile on a USB drive to protect an Ubuntu install using full disk encryption with dm-crypt,LUKS? Not to have the system decryptable by either the password OR the keyfile, but to require both to decrypt. It is extremely useful for a situation where you are forced to provide the password, as the attacker is still unable to decrypt the data.

---

### Post by sky114 on 2013-06-24
I've wanted to do the same,  the way I've done it is by keeping a keyfile on a password protected (LUKS encrypted) USB drive. So I've used my password to decrypt the keyfile and then used that to open my data volume, with a small script one can open the volumes in one step.

Edit: But it would be nice with a more straight forward solution, where you do not have risk of an attacker stealing the decrypted keyfile  and thus being able to open the data volume without the password.

---

