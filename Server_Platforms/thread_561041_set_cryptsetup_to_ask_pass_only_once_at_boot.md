---
title: "set cryptsetup to ask pass only once at boot"
date: 2007-09-27
forum: Server Platforms
---

### Post by qwels on 2007-09-27
Hi! 
I just set up two partitions with cryptsetup (dm-crypt and luks).
Since they have the same password set I wonder if I could avoid typing in the password twice.

Also, is it possible to hide the algorithm and hash used for the encryption as with loop-aes and truecrypt? 
Thanks

---

### Post by /etc/init.d/ on 2007-09-27
> **qwels said:**
> Also, is it possible to hide the algorithm and hash used for the encryption as with loop-aes and truecrypt? 

dm_crypt was not designed to be used for plausible deniability, so this is unfortunately not possible.

---

### Post by cprise on 2007-09-30
> **/etc/init.d/ said:**
> dm_crypt was not designed to be used for plausible deniability, so this is unfortunately not possible.
I think you mean LUKS-dmcrypt, not dmcrypt by itself.

---

### Post by /etc/init.d/ on 2007-09-30
> I think you mean LUKS-dmcrypt, not dmcrypt by itself.
Oops, yes, I meant dm_crypt with LUKS.

---

