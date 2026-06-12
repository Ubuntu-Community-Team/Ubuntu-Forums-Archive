---
title: "Recovering data from corrupt encrypted partition"
date: 2010-02-25
forum: Security
---

### Post by Baneblade on 2010-02-25
I have recently recovered from an HDD failure on my Drobo. One of the disks died and corrupted the entire array  (which is not supposed to happen). I have since managed to copy the data off onto smaller disks and after replacing the failed drive, have copied everything back.

Now that im up and running again, i was wondering how this situation would play out on encrypted disks, or in the case of a drobo a large encrypted partition (as you cannot encrypt the entire array).

Would i still be able to recover the data if i were to encrypt it? It is a 4.2TB array, and i assume that I would need to copy the data in its entirety to recover it, so using multiple smaller disks would be out of the question right?

---

### Post by bodhi.zazen on 2010-02-25
I do not know for sure, perhaps we will hear from someone with more experience, but I would guess encryption adds a whole new layer of complexity.

---

### Post by Baneblade on 2010-02-27
Ok perhaps that was a bit much :p

Taking it down to basics then.. 
Using Truecrypt: if i have a simple EXT4/NTFS disk with an encrypted virtual disk on it and this becomes corrupt, will i be able to recover the data assuming I have the correct password to unlock and mount the volume.

---

### Post by Baneblade on 2010-03-02
Bump?

---

### Post by bodhi.zazen on 2010-03-02
If your partition is corrupted you can loose data, with or without the use of truecrypt or any other encryption.

Encryption will make it more difficult for data recovery tools.

So with encryption you will be more likely to lose data if your partition or hard drive is corrupt if nothing else then simply because the data is more complex.

For example, take a look at Photorec. Try running photorec or testdisk on both an encrypted and an unencrypted partition. The difference in complexity should be immediately obvious to you.

---

### Post by Baneblade on 2010-03-02
Thank you, that's made it much clearer for me. :)

---

