---
title: "Encrypted LVM defaults"
date: 2009-04-25
forum: Security
---

### Post by dr_pressure on 2009-04-25
Hi quick question, if I set up my server install with encrypted lvm:

-which crypto and hash algorithms are used?
-how can i change the password later?


thanks!

---

### Post by Steven3k on 2009-04-25
Hi

Crypto: aes 256bit key, cbc-essiv
Hash: sha1

You can change the password using:

```

sudo cryptseyup luksAddKey /dev/sdX

```to add a new key, and

```

sudo cryptsetup luksKillSlot /dev/sdX Y

```to delete the old one. Y is the slot number where the key is stored. The first time it will be 0. Each time you mount a drive using a key cryptsetup will tell you which slot it will unlock.

HTH

---

### Post by dr_pressure on 2009-04-25
Thanks very much :D

---

### Post by kevdog on 2009-04-26
Is there a different hash you can use beyond sha1

---

### Post by unutbu on 2009-04-26
From the cryptsetup man page:
```
NOTES ON PASSWORD PROCESSING FOR LUKS
       LUKS will always use SHA1 in HMAC mode, and no other mode 
       is supported at the moment.
       Hence, -h is ignored.
```

---

### Post by kevdog on 2009-04-26
Those creators need to catch up with the times.  SHA1 weaknesses have been well exposed.

---

### Post by unutbu on 2009-04-26
Does this mean a LUKS encrypted partition is crackable?
Can you point me to more info on the vulnerability?

Edit: My question is answered here: [http://www.schneier.com/blog/archives/2005/02/cryptanalysis_o.html](http://www.schneier.com/blog/archives/2005/02/cryptanalysis_o.html)

---

