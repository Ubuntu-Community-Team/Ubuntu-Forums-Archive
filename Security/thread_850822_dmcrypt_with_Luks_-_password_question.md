---
title: "dmcrypt with Luks - password question"
date: 2008-07-06
forum: Security
---

### Post by systemdowned on 2008-07-06
I plan on moving my home server's hard drives to an encryption setup with dm-crypt and luks. I tested everything out in a virtual machine and everything works like a charm. 

My Question:
I want to use the same password for my hard drives. Is there any way to set it up so it only asks for the password once at boot to mount all the hard drives?

---

### Post by hyper_ch on 2008-07-06
there is ;) I wrote a little howto for that...

---

### Post by Meson on 2008-07-06
> **hyper_ch said:**
> there is ;) I wrote a little howto for that...

In addition to his guide (which is here: [http://ubuntuforums.org/showthread.php?t=837416](http://ubuntuforums.org/showthread.php?t=837416)) you can do something like create a small partition to store the keyfiles and encrypt that partition with a passphrase.

---

### Post by systemdowned on 2008-07-06
Thanks!

---

### Post by hyper_ch on 2008-07-07
what would that small partition be good for?

---

### Post by Meson on 2008-07-07
> **hyper_ch said:**
> what would that small partition be good for?

A lot of people encrypt a usb flash drive with a password.  The flash drive stores keys for their various encrypted partitions.  When they boot up they only need to enter a password to decrypt the flash drive, making the keys available to decrypt the computer's partitions.

For convenience he could just store the keys on his own computer under a passworded encrypted partition.  Your method is fine, but if you want different encryption schemes then storing the key for one partition on the root partition is counterproductive.

For example, I like to use a lower-grade encryption for maximum speed on my root partition, but then the highest possible grade for my home partition.  If I stored the key for my home partition on my root partition, the different encryption settings would be worthless - they might as well all be the lowest.

---

### Post by hyper_ch on 2008-07-07
ok :)

---

