---
title: "encrypted disk with hibernate"
date: 2016-10-07
forum: Security
---

### Post by deb2014 on 2016-10-07
Hello,I installed ubuntu 16.04 by making a full encryption disk as advocated on several tutorials : one fully encrypted partition with LVM (swap, / (root) and /home), one free partition for /boot.


Trouble is that resuming from hibernation from the encrypted swap leads to random freezes, I could not solve this issue and to get hibernating stable, I had to create another free partition, a free swap from which hibernation/resume works fine.


But I lost the security of being asked the luks passphrase at resuming from hibernation. I assume it is kept in memory, written to the free swap when hibernating.I put a screen lock before hibernating but that is not enough secure for me. Is there a way to make cryptsetup lose the luks key before hibernating (just before going off) so that it hasto ask it on resuming in order to read / and /home, just as if the swap was encrypted ? or prevent cryptsetup to write the key to the free swap ?


Thanks for your help or any advices to make hibernate more secure.


Regards

---

### Post by DuckHook on 2016-10-07
When you broke the encrypted swap and reconfigured swap with an unencrypted partition, it does not hold your password in RAM or get written to the swap itself&#8213;it simply hibernates without encryption. And since an unencrypted swap is basically an open book to any disk scanner/recovery tool, there is no point in setting a password.

If you want to re-encrypt your swap partition and allow hibernation, follow the steps in the following guide: [https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap](https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap)

---

