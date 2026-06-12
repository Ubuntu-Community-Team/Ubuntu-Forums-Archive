---
title: "How to change cryptsetup full-disk-encryption passphrase?"
date: 2009-03-27
forum: Security
---

### Post by peterzh on 2009-03-27
> peter@petercomp:~$ sudo cryptsetup status sda3_crypt
/dev/mapper/sda3_crypt is active:
  cipher:  aes-cbc-essiv:sha256
  keysize: 256 bits
  device:  /dev/sda3
  offset:  2056 sectors
  size:    209983559 sectors
  mode:    read/write

How would I go about changing the passphrase for this device? I know the current passphrase.

Also is it possible to change the string outputted on startup? It normally says something like "Please enter the passphrase to unlock encrypted device UUID-<randomstuffhere>"?

Any help would be appreciated

---

### Post by hyper_ch on 2009-03-28
changing luks passwords involves two steps:

(1) adding a new one
(2) delete the old one

You have 12 slots (or 15) which you can use for different passwords/keyfiles to unlock the partition. The rationale because you cannot change it but must add and then revmove is simple: it prevents you from accidentally deteling/altering a passphrase so that you won't lose access.

See step X of my guide here:  [http://www.howtoforge.com/ubuntu_dm_crypt_luks](http://www.howtoforge.com/ubuntu_dm_crypt_luks)

---

### Post by peterzh on 2009-03-29
Great. Thank you very much. :popcorn:

---

### Post by anirudh.srivathsa on 2011-06-29
If i change the  passphrase for encrypting the system, will it affect the key generated?  will it affect the data present in the system?

---

